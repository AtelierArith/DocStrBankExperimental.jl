```
update_j4_mean_elements_epoch(orb::KeplerianElements, new_epoch::Union{Number, DateTime}) -> KepleriranElements
```

平均要素 `orb` のエポックを J4 軌道伝播器を使用して `new_epoch` に更新します。`new_epoch` はユリウス日または `DateTime` で表すことができます。

!!! note
    このアルゴリズムのバージョンは、デフォルトの定数 `j4c_egm2008` を使用して新しい J4 伝播器を割り当てます。別の定数セットが必要な場合は、代わりに関数 [`update_j4osc_mean_elements_epoch!`](@ref) を使用してください。


# 例

```julia-repl
julia> orb = KeplerianElements(
           DateTime("2023-01-01") |> datetime2julian,
           7190.982e3,
           0.001111,
           98.405 |> deg2rad,
           90     |> deg2rad,
           200    |> deg2rad,
           45     |> deg2rad
       )
KeplerianElements{Float64, Float64}:
           Epoch :    2.45995e6 (2023-01-01T00:00:00)
 Semi-major axis : 7190.98     km
    Eccentricity :    0.001111
     Inclination :   98.405    °
            RAAN :   90.0      °
 Arg. of Perigee :  200.0      °
    True Anomaly :   45.0      °

julia> update_j4_mean_elements_epoch(orb, DateTime("2023-01-02"))
KeplerianElements{Float64, Float64}:
           Epoch :    2.45995e6 (2023-01-02T00:00:00)
 Semi-major axis : 7190.98     km
    Eccentricity :    0.001111
     Inclination :   98.405    °
            RAAN :   90.9555   °
 Arg. of Perigee :  197.079    °
    True Anomaly :  127.293    °
```
