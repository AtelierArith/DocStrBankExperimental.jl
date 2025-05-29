```
R2Q(R [, area = dt * 3.6, dt = 24])
Q2R(Q [, area = dt * 3.6, dt = 24])
```

Convert runoff from mm per dt to flow rate in m³/s.

## Arguments

  * `R::Real`: Runoff (mm per dt).
  * `Q::Real`: Flow rate in m³/s.
  * `area::Real`: Basin area in km². Default is `dt * 3.6`.
  * `dt::Real`: Time duration in hours. Default is 24.

## Returns

Flow rate in m³/s.
