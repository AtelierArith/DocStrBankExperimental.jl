```
algorithm2_1_algorithm3!(p::Vector{T}, I::Vector{Int}, w::Vector{<:Real}, u::Real) where {T<:Real}
```

`w[I]`を確率に正規化し、その結果を`p`に格納します。次に、`w[I]`の中でゼロに等しい0個以上の要素に確率質量`0 ≤ u ≤ 1`を分配します。もし`w[I]`のすべての値がゼロであり、`u ≠ 0`の場合、`p`は均等な確率質量で満たされます。`T`は`inv(one(T))`の結果を保持できる型でなければなりません。

参照: [`algorithm2_1_algorithm3`](@ref)

# 例

```jldoctest
julia> I = [1, 2, 5, 6]; w = [10, 0, 30, 40, 0, 20]; u = 0.5;

julia> algorithm2_1_algorithm3!(similar(I, Rational{Int}), I, w, u)
4-element Vector{Rational{Int64}}:
 1//6
 1//4
 1//4
 1//3
```
