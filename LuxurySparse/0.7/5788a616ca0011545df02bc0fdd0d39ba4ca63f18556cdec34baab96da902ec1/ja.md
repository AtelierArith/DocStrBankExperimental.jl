```
IMatrix{Tv}

IMatrix(n) -> IMatrix
IMatrix(A::AbstractMatrix{T}) where T -> IMatrix
```

サイズ `n` の単位行列を表します。デフォルトの型は `Int64` です。`*` と `kron` の両方が最適化されています。

# 例

```julia-repl
julia> IMatrix(4)
4×4 IMatrix{Bool}:
 1  0  0  0
 0  1  0  0
 0  0  1  0
 0  0  0  1

julia> IMatrix(rand(4,4))
4×4 IMatrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0
 0.0  0.0  0.0  1.0

```
