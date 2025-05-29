```
xkb_state_led_index_is_active(state, idx)
```

指定されたキーボード状態において、インデックスによってLEDがアクティブかどうかをテストします。

### 戻り値

LEDがアクティブな場合は1、そうでない場合は0を返します。LEDインデックスがキーマップで有効でない場合は-1を返します。

### 参照

[`xkb_led_index_t`](@ref) xkb_state
