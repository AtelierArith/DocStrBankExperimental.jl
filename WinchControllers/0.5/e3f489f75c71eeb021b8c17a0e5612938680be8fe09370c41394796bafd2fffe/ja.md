```
mutable struct CalcVSetIn
```

ソフトスイッチングを使用した計算 `v_set_in` のコンポーネント。

## フィールド

  * wcs::[WCSettings](@ref)
  * mixer2::[Mixer_2CH](@ref): ミキサーコンポーネント。デフォルト: `Mixer_2CH(wcs.dt, wcs.t_blend)`
  * input_a: デフォルト: 0
  * input_b: デフォルト: 0
