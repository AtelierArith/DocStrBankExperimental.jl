```
effective_variables(p::AbstractPolynomialLike)
```

非ゼロ次数を持つ項が少なくとも1つあるすべての変数を含む、`eltype` `variable_union_type(p)` (see [`variable_union_type`](@ref)) のベクトルを返します。つまり、`maxdegree(p, v)` がゼロでないすべての変数 `v` を返します。返されるベクトルは降順にソートされています。
