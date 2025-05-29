```
Stick(dpara::Float64, t2::Float64)
```

平行拡散率 `dpara` と T2 緩和時間 `t2` を持つ Stick 型オブジェクトを返します。Stick モデルの垂直拡散率はゼロです。

# 例

```julia-repl
julia> Stick(dpara = 1.7e-6, t2 = 60e-3)
Stick(1.7e-6, 0.06)
```
