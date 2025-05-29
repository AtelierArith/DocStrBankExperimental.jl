```julia
total_mino_time(
    metric::Krang.Kerr{T},
    roots::NTuple{4, T} where T
) -> Any

```

レイに沿って蓄積できる最大のミノ時間を返します。

# 引数

  * `metric` : カー metric
  * `roots` : 放射ポテンシャルの根
  * `I0_inf` : 無限大でのミノ時間
