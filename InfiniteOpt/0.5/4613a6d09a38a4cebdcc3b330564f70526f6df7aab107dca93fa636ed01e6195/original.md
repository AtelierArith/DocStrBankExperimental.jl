```
@deriv(expr, pref_expr1[, ...]
       )::Union{JuMP.AbstractJuMPScalar, Float64}
```

The macro variant of [`deriv`](@ref) that is more efficient for expression building  and enables symbolic differential operator parameter defintions via `pref_expr`s.  Like `deriv` expr can be any InfiniteOpt expression and the appropriate calculus  rules will applied to `expr` to take its derivative with respect to the indicated  infinite parameters detailed by the `pref_expr`s. The resulting derivative  expression will contain individual derivatives that were created and added to the  InfiniteModel as needed. Here each `pref_expr` arugment can be of the form:

  * `pref::GeneralVariableRef`: An indiviudal infinite parameter reference
  * `(pref::GeneralVariableRef)^(p::Int)`: An infinite parameter applied `p` times.

Thus, the syntax `@deriv(expr, pref^2)` is equivalent to `@deriv(expr, pref, pref)`. 

This will error if `pref_expr` is an unrecongnized syntax, no infinite parameter  is given, or if any of the specified parameters are not infinite.

**Example**

```julia-repl
julia> @infinite_parameter(m, t in [0, 1])
t

julia> @variable(m, x, Infinite(t))
x(t)

julia> @variable(m, z)
z

julia> deriv_expr = @deriv(x^2 + z, t^2)
2 ∂/∂t[∂/∂t[x(t)]]*x(t) + 2 ∂/∂t[x(t)]²
```
