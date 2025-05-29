```
DestructuredAssigmentExpr{E}(; lhs_names::Vector{Symbol}, destructure_type::Symbol, rhs::E)
```

Matches an expression of the form `lhs = rhs`, where 

  * if `destructure_type == :tuple`, `lhs` is of the form `Expr(:tuple, lhs_names[1:end-1]..., Expr(:(=), lhs_names[end], rhs)`
  * if `destructure_type == :eq_tuple`, `lhs` is of the form `(lhs_names...) = rhs`
  * if `destructure_type == :eq_namedtuple`, `lhs` is of the form `(; lhs_names...) = rhs`
