```
toeplitz(a::Vector{T}) where T
```

ベクトル `a` をトポリッツ行列に変換します。

# 例

```julia-repl
julia> a = [1, 2, 3]; toeplitz(a)
2×2 Matrix{Int64}:
 2  1
 3  2
```
