```
algorithm3_ratio!(p::Vector{T}, w::Vector{<:Real}, r::Real) where {T<:Real}
```

`w`を確率に正規化し、その結果を`p`に格納します。次に、0またはそれ以上の`w`の要素に確率質量`u = r / (1 + r)`を分配し、(初めは)ゼロの要素の合計と非ゼロの要素の合計の比が`r`になるようにします。`T`は`inv(one(T))`の結果を保持できる型でなければなりません。

# 例

```jldoctest
julia> w = [0, 10, 5, 1]; r = 1.0;

julia> algorithm3_ratio!(similar(w, Float64), w, r)
4-element Vector{Float64}:
 0.5
 0.3125
 0.15625
 0.03125
```
