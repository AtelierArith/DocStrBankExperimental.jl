```
matrix(R::Ring, r::Int, c::Int, arr::AbstractVector{T}) where {T}
```

$$
R
$$

上の$r \times c$行列を構築します。エントリは`arr`から行ごとに取得されます。
