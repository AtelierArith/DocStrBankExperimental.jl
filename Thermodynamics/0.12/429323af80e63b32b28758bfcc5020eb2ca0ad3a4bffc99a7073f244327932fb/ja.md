```
PhasePartition
```

湿った空気混合物の質量分率を表します。

# コンストラクタ

```
PhasePartition(q_tot::Real[, q_liq::Real[, q_ice::Real]])
PhasePartition(param_set::APS, ts::ThermodynamicState)
```

[`PhasePartition_equil`](@ref) も参照してください。

# フィールド

  * `tot`: 総比湿
  * `liq`: 液体水の比湿 (デフォルト: `0`)
  * `ice`: 氷の比湿 (デフォルト: `0`)
