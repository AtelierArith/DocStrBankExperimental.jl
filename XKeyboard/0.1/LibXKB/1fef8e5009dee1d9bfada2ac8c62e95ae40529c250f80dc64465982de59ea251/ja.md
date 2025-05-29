```
xkb_state_led_name_is_active(state, name)
```

指定されたキーボード状態において、名前でLEDがアクティブかどうかをテストします。

### 戻り値

LEDがアクティブな場合は1、そうでない場合は0を返します。この名前のLEDがキーマップに存在しない場合は-1を返します。

### 参照

[`xkb_led_index_t`](@ref) xkb_state
