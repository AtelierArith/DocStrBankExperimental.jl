```
deriv(expr::JuMP.AbstractJuMPScalar, pref1::GeneralVariableRef[, ....]
      )::Union{JuMP.AbstractJuMPScalar, Float64}
```

Apply appropriate calculus methods to define and return the derivative expression of `expr`  with respect to the infinite parameter(s) `pref1`, pref2`, etc. in that respective  order. This will implicilty build and add individual [`Derivative`](@ref)s as  appropriate. Errors if no infinite parameter is given or if the parameters are  not infinite.

**Example**

```julia-repl
julia> @infinite_parameter(m, t in [0, 1])
t

julia> @variable(m, x, Infinite(t))
x(t)

julia> @variable(m, z)
z

julia> deriv_expr = deriv(x^2 + z, t, t)
2 ∂/∂t[∂/∂t[x(t)]]*x(t) + 2 ∂/∂t[x(t)]²
```
