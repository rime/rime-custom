# rime-custom

[Rime](http://rime.im) 輸入法自定義配置

授權條款：見 [LICENSE](LICENSE)

可通過 [東風破](https://github.com/rime/plum) 安裝以下配方：

## 添加輸入方案到方案選單

參數化配方： ℞ **custom:add**:schema=...

示例：

```bash
# 配方參數：已安裝的輸入方案標識
schema=luna_pinyin

# 使用配方，將參數代入，可以一行命令完成
bash rime-install custom:add:schema=${schema}
```

## 清空輸入方案列表

配方： ℞ **custom:clear_schema_list**

清除在默認配置中啓用的輸入方案，方便以逐項添加的方式重新定義輸入方案列表。

## 設定單項配置

參數化配方： ℞ **custom:set**:config=...,key=...,value=...

示例：

```bash
# 配方參數：配置文件名（不含 `.yaml` 後綴）
config=default
# 配方參數：欲設定配置項的節點路徑
key=menu/page_size
# 配方參數：配置項的值，可以是數值、邏輯值，或不包含特殊字符的字符串值
value=3

# 使用配方，將參數代入，可以一行命令完成
bash rime-install custom:set:config=${config},key=${key},value=${value}
```

使用這道配方，須瞭解原配置文件的結構和內容，並熟悉 [Rime 配置文件](http://github.com/rime/home/wiki/Configuration) 的自定義方法。

## 按鍵綁定

參數化配方： ℞ **custom:use_key_bindings**:feature=...

追加一組按鍵綁定到 `key_binder/bindings`，以實現變量 `feature` 所指定的功能。

可選的按鍵綁定詳見 [key_bindings.yaml](https://github.com/rime/rime-prelude/blob/master/key_bindings.yaml) 的定義。

## 狀態切換鍵

參數化配方： ℞ **custom:use_switch_key**:shift=...,control=...,caps=...,lock=...

定製各個狀態切換鍵的行爲，以及是否使用大寫鎖定的選項。

示例：禁用 Shift、使用 Caps Lock 切換中／西文狀態而非大寫鎖定

```bash
bash rime-install custom:use_switch_key:shift=noop,lock=false
```

## 使用擴展符號

參數化配方： ℞ **custom:use_symbols**:schema=...

爲輸入方案啓用擴展符號支持。

通過形如 `/a`、`/1`、`/jt` 的助記符輸入類似帶變音符號的拉丁字母、風格數字、箭頭等特殊符號。
