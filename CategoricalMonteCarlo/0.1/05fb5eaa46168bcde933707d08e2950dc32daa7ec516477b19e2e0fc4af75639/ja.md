```
algorithm2_1_algorithm3!(p::Vector{T}, I::Vector{Int}, w::Vector{<:Real}, u::Real) where {T<:Real}
```

`w[I]`を確率に正規化し、その結果を`p`に格納します。次に、`w[I]`の中でゼロに等しい0個以上の要素に確率質量`u = r / (1 + r)`を分配します。このとき、(初めは)ゼロの要素の合計と非ゼロの要素の合計の比が`r`に等しくなるようにします。`T`は`inv(one(T))`の結果を保持できる型でなければなりません。

参照: [`algorithm2_1_algorithm3_ratio`](@ref), [`algorithm2_1!`](@ref),  [`algorithm3_ratio!`](@ref)

# 例

```jldoctest
julia> I = [1, 2, 5, 6]; w = [10, 0, 30, 40, 0, 20]; r = 1.0;

julia> algorithm2_1_algorithm3_ratio!(similar(I, Rational{Int}), I, w, r)
4-element Vector{Rational{Int64}}:
 1//6
 1//4
 1//4
 1//3
```
