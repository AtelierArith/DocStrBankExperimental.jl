```
algorithm3!(p::Vector{T}, w::Vector{<:Real}, u::Real) where {T<:Real}
```

`w`を確率に正規化し、結果を`p`に格納します。`0 ≤ u ≤ 1`の確率質量を`w`の中でゼロに等しい0個以上の要素に分配します。もし`w`のすべての値がゼロで`u ≠ 0`の場合、`p`は均等な確率質量で満たされます。`T`は`inv(one(T))`の結果を保持できる型でなければなりません。

# 例

```jldoctest
julia> w = [0, 10, 5, 1]; u = 0.5;

julia> algorithm3!(similar(w, Float64), w, u)
4-element Vector{Float64}:
 0.5
 0.3125
 0.15625
 0.03125
```
