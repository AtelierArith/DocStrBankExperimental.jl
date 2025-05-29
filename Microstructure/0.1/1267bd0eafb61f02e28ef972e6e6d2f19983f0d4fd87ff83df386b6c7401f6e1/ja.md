```
Cylinder(
    da::Float64, 
    dpara::Float64, 
    d0::Float64, 
    t2::Float64
    )
```

円柱直径 `da`、平行拡散率 `dpara`、内因性拡散率 `d0`、および T2 緩和時間 `t2` を持つ Cylinder 型オブジェクトを返します。

# 例

```julia-repl
julia> Cylinder(da = 3.0e-6, dpara = 1.8e-9, d0 = 1.7e-9, t2 = 90e-3)
Cylinder(3.0e-6, 1.8e-9, 1.7e-9, 0.09)
```
