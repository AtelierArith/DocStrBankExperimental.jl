```
variable_bound_info(vref::JuMP.AbstractVariableRef)::Tuple{<:Number, <:Number}
```

再定式化手法を実装するために必要な `(lower_bound, upper_bound)` の形式のタプルを返します。 [`requires_variable_bound_info`](@ref) が実装されている場合にのみ機能します。
