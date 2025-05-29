```
algorithm3!(p::Vector{T}, u::Real) where {T<:Real}
```

`p`を確率に正規化し、0またはそれ以上の要素の中で0に等しい`p`に確率質量`u`を分配します。もし`w`のすべての値がゼロであり、`u ≠ 0`の場合、`p`は均一な確率質量で満たされます。`T`は`inv(one(T))`の結果を保持できる型でなければなりません。

参照: [`algorithm3`](@ref), [`algorithm3_ratio!`](@ref)

# 例

```jldoctest
julia> algorithm3!(Rational{Int}[0, 10, 5, 0], 0.5)
4-element Vector{Rational{Int64}}:
 1//4
 1//3
 1//6
 1//4
```
