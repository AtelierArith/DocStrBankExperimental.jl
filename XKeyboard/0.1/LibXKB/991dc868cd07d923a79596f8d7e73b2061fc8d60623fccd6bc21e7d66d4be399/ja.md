```
xkb_keymap_num_leds(keymap)
```

キーマップ内のLEDの数を取得します。

!!! warning
    範囲 [ 0...[`xkb_keymap_num_leds`](@ref)() ) はキーマップ内のすべてのLEDを含みますが、非アクティブなLEDも含まれる可能性があります。この範囲を反復処理する際には、[`xkb_keymap_led_get_name`](@ref)() や [`xkb_state_led_index_is_active`](@ref)() などの関数を呼び出す際にこのケースを処理する必要があります。


### 参照

[`xkb_led_index_t`](@ref) xkb_keymap
