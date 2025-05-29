```
algorithm3_ratio!(p::Vector{T}, r::Real) where {T<:Real}
```

`p`を確率に正規化し、確率質量`u = r / (1 + r)`を`p`の0またはそれ以上の要素に分配します。このとき、(初めは)ゼロの要素の合計と非ゼロの要素の合計の比が`r`に等しくなるようにします。`T`は`inv(one(T))`の結果を保持できる型でなければなりません。

参照: [`algorithm3_ratio`](@ref), [`algorithm3!`](@ref)
