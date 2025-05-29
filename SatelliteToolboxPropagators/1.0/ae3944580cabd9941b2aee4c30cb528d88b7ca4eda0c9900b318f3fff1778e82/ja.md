```
update_j2_mean_elements_epoch!(j2d::J2Propagator, orb::KeplerianElements, new_epoch::Union{Number, DateTime}) -> KepleriranElements
```

平均要素 `orb` のエポックを、ジュリア日または `DateTime` で表される `new_epoch` に、推進器 `j2d` を使用して更新します。

!!! note
    J2軌道推進器 `j2d` は、関数によって返されるケプラー要素で初期化されます。


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

# 作成したケプラー要素を使用して新しいJ2軌道推進器を割り当てます。ここでは、任意の
# ケプラー要素のセットを使用できます。
julia> j2d = j2_init(orb);

julia> update_j2_mean_elements_epoch!(j2d, orb, DateTime("2023-01-02"))
KeplerianElements{Float64, Float64}:
           Epoch :    2.45995e6 (2023-01-02T00:00:00)
 Semi-major axis : 7190.98     km
    Eccentricity :    0.001111
     Inclination :   98.405    °
            RAAN :   90.9565   °
 Arg. of Perigee :  197.078    °
    True Anomaly :  127.291    °
```
