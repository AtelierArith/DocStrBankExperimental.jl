```
set_variable_bound_info(vref, method::AbstractReformulationMethod)::Tuple{<:Number, <:Number}
```

`method` が不等式を再定式化するために必要な境界情報である `(lower_bound, upper_bound)` の形式のタプルを返します。これは、`requires_variable_bound_info(method) = true` である `methods` のみ実装する必要があります。これらの境界は後で [`variable_bound_info`](@ref) を介してアクセスできます。
