```
onaxis(Ak, Q::QDHT; dim=Q.dim)
```

空間内の軸上サンプルを計算します（すなわち、r=0で）変換された配列 `Ak` から。

!!! note
    `onaxis` は現在、0次変換のみサポートされています


# 例

```jldoctest
julia> q = QDHT{0, 1}(10, 128); A = exp.(-q.r.^2/2);
julia> onaxis(q*A, q) ≈ 1 # は exp(0) = 1 であるべき
true
```
