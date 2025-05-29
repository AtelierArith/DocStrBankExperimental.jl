```
signal(spin)
signal(M)
```

与えられたスピンまたは磁化ベクトルから検出された信号を返します。

# 例

```jldoctest
julia> signal(Spin(Magnetization(1, 2, 3), 1, 1000, 100, 0))
1.0 + 2.0im

julia> signal(MagnetizationMC((1, 2, 3), (1, 1, 1)))
2 + 3im
```
