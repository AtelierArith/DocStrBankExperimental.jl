```
conversion_type(a::Space, b::Space)
```

Return a `Space` that has a banded [`Conversion`](@ref) operator to both `a` and `b`. Override `ApproxFun.conversion_rule` when adding new `Conversion` operators.

See also [`maxspace`](@ref)
