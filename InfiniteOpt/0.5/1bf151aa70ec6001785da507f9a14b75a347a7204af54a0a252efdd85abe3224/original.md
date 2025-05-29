```
evaluate_all_derivatives!(model::InfiniteModel)::Nothing
```

Evaluate all the derivatives in `model` by adding the corresponding auxiliary  equations to `model`. See [`evaluate`](@ref) for more information.

**Example**

```julia-repl
julia> m = InfiniteModel();

julia> @infinite_parameter(m, t in [0,2], supports = [0, 1, 2]);

julia> @infinite_parameter(m, x in [0,1], supports = [0, 0.5, 1]);

julia> @variable(m, T, Infinite(x, t));

julia> dref1 = @deriv(T, t); dref2 = @deriv(T, x^2);

julia> evaluate_all_derivatives!(m)

julia> print(m)
Feasibility
Subject to
 ∂/∂t[T(x, t)](x, 1) - T(x, 1) + T(x, 0) = 0.0, ∀ x ∈ [0, 1]
 ∂/∂t[T(x, t)](x, 2) - T(x, 2) + T(x, 1) = 0.0, ∀ x ∈ [0, 1]
 0.5 ∂/∂x[T(x, t)](0.5, t) - T(0.5, t) + T(0, t) = 0.0, ∀ t ∈ [0, 2]
 0.5 ∂/∂x[T(x, t)](1, t) - T(1, t) + T(0.5, t) = 0.0, ∀ t ∈ [0, 2]
 0.5 ∂/∂x[∂/∂x[T(x, t)]](0.5, t) - ∂/∂x[T(x, t)](0.5, t) + ∂/∂x[T(x, t)](0, t) = 0.0, ∀ t ∈ [0, 2]
 0.5 ∂/∂x[∂/∂x[T(x, t)]](1, t) - ∂/∂x[T(x, t)](1, t) + ∂/∂x[T(x, t)](0.5, t) = 0.0, ∀ t ∈ [0, 2]
```
