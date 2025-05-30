```
effective_variables(p::AbstractPolynomialLike)
```

非ゼロ次数を持つすべての変数を含む `eltype` `variable_union_type(p)` のベクターを返します（[`variable_union_type`](@ref)を参照）。つまり、`maxdegree(p, v)` がゼロでないすべての変数 `v` を返します。返されるベクターは降順にソートされています。
