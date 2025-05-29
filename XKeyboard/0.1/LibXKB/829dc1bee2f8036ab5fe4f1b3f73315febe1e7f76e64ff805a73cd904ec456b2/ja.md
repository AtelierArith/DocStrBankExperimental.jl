```
xkb_keymap_led_get_index(keymap, name)
```

名前によるLEDのインデックスを取得します。

xkb_keymap

### 戻り値

インデックス。指定された名前のLEDが存在しない場合は、[`XKB_LED_INVALID`](@ref)を返します。
