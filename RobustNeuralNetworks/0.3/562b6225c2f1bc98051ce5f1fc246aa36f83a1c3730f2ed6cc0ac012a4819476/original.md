```
REN(ps::AbstractRENParams{T}) where T
```

Construct a REN from its direct parameterisation.

This constructor takes a direct parameterisation of REN (eg: a [`GeneralRENParams`](@ref) instance) and converts it to a **callable** explicit parameterisation of the REN. An example can be found in the docs for [`AbstractREN`](@ref).

See also [`AbstractREN`](@ref), [`WrapREN`](@ref), and [`DiffREN`](@ref).
