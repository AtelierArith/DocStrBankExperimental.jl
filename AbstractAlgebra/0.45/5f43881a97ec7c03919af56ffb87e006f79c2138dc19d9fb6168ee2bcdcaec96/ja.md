```
matrix(R::Ring, arr::AbstractMatrix{T}) where {T}
```

$$
R
$$

上の行列を `arr` のエントリを持つように構築します。

# 例

```jldoctest
julia> matrix(GF(3), [1 2 ; 3 4])
[1   2]
[0   1]

julia> using LinearAlgebra ; matrix(GF(5), I(2))
[1   0]
[0   1]
```
