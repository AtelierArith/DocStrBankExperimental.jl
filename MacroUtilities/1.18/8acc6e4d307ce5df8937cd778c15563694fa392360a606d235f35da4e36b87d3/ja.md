```
DestructuredAssigmentExpr{E}(; lhs_names::Vector{Symbol}, destructure_type::Symbol, rhs::E)
```

`lhs = rhs` の形の式に一致します。ここで、

  * `destructure_type == :tuple` の場合、`lhs` は `Expr(:tuple, lhs_names[1:end-1]..., Expr(:(=), lhs_names[end], rhs)` の形です。
  * `destructure_type == :eq_tuple` の場合、`lhs` は `(lhs_names...) = rhs` の形です。
  * `destructure_type == :eq_namedtuple` の場合、`lhs` は `(; lhs_names...) = rhs` の形です。
