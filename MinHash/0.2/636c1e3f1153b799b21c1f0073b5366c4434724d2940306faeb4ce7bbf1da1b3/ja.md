```
intersectionlength(v::AbstractVector{MinHashSketch})
```

`length(v)` の平方 `Matrix{Int}` を返します。ここで、`[i, j]` で `i > j` のセルには、`v[i]` と `v[j]` の両方に含まれるハッシュの数が含まれます。

# 例

```julia-repl
julia> v = [sketch((1:1000) .+ (300*i), 100) for i in 1:4];

julia> intersectionlength(v)
4×4 Array{Int64,2}:
  0   0   0  0
 64   0   0  0
 27  58   0  0
  8  34  73  0
```
