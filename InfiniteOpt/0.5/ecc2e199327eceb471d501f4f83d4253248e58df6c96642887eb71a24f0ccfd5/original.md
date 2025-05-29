```
evaluate(dref::DerivativeRef)::Nothing
```

Numerically evaluate `dref` by computing its auxiliary derivative constraints  (e.g., collocation equations) and add them to the model. For normal usage, it is  recommended that this method not be called directly and instead have TranscriptionOpt  handle these equations. Errors if `evaluate_derivative` is not  defined for the derivative method employed.

The resulting constraints can be accessed via `derivative_constraints`.

**Example**

```julia-repl
julia> m = InfiniteModel(); @infinite_parameter(m, t in [0,2]); @variable(m, T, Infinite(t));

julia> dref = @deriv(T,t)
∂/∂t[T(t)]

julia> add_supports(t, [0, 0.5, 1, 1.5, 2])

julia> evaluate(dref)

julia> derivative_constraints(dref)
Feasibility
4-element Array{InfOptConstraintRef,1}:
 0.5 ∂/∂t[T(t)](0.5) - T(0.5) + T(0) = 0.0
 0.5 ∂/∂t[T(t)](1) - T(1) + T(0.5) = 0.0
 0.5 ∂/∂t[T(t)](1.5) - T(1.5) + T(1) = 0.0
 0.5 ∂/∂t[T(t)](2) - T(2) + T(1.5) = 0.0
```
