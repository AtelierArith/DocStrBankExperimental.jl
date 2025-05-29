```
Sphere(
    diff::Float64, 
    size::Float64, 
    t2::Float64
    )
```

球内の拡散率 `diff`、球の半径 `size`、および T2 緩和時間 `t2` を持つ Sphere 型オブジェクトを返します。

# 例

```julia-repl
julia> Sphere(diff = 3.0e-9, size = 8.0e-6, t2 = 45e-3)
Sphere(3.0e-9, 8.0e-6, 0.045)
```
