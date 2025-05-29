```
Zeppelin(
    dpara::Float64, 
    dperp_frac::Float64, 
    t2::Float64
    )
```

平行拡散率 `dpara`、平行拡散率の割合として表される軸対称の垂直拡散率 `dperp_frac`、および T2 緩和時間 `t2` を持つ Zeppelin タイプのオブジェクトを返します。

# 例

```julia-repl
julia> Zeppelin(dpara = 1.7e-6, dperp_frac = 0.5, t2 = 0.0)
Zeppelin(1.7e-6, 0.5, 0.0)
```
