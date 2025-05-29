```
InterceptTerm{HasIntercept} <: AbstractTerm
```

Represents the presence or (explicit) absence of an "intercept" term in a regression model.  These terms are generated from [`ConstantTerm`](@ref)s in a formula by `apply_schema(::ConstantTerm, schema, ::Type{<:StatisticalModel})`. A `1` yields `InterceptTerm{true}`, and `0` or `-1` yield `InterceptTerm{false}` (which explicitly omits an intercept for models which implicitly includes one via the [`implicit_intercept`](@ref) trait).
