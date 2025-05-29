```
matrixrepr(f, b1::AbstractBasis, b0::AbstractBasis, ::Type{R})) where R
```

線形写像 `f` を基底 `b0` (ソース) と `b1` (ターゲット) に関して表す行列を返します。係数の型は `R` です。

[`matrixrepr!`](@ref) も参照してください。

# 例

```jldoctest
julia> @linear f; f(x) = Linear(uppercase(x) => 1, 'A' => 1)
f (generic function with 2 methods)

julia> matrixrepr(f, Basis('A':'C'), Basis('a':'c'), Int)
3×3 Matrix{Int64}:
 2  1  1
 0  1  0
 0  0  1
```
