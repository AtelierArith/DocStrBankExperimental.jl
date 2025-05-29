```
Options(; metaprogramming::Bool = true, μ::Real = 1, ϵ::Real = eps(), A_init_value::Real = 1.0, A_lower::Union{Real, Nothing} = nothing, A_upper::Union{Real, Nothing} = nothing, A_use_sobol::Bool = false, V_init_value::Real = 1.0, V_lower::Union{Real, Nothing} = nothing, V_upper::Union{Real, Nothing} = nothing, V_use_sobol::Bool = false, low = -1e10, high = 1e10, tol = 1e-10, maxiter = 1e6)
```

Defines a struct `Options` for configuring various parameters used in optimization and calculus. It provides flexible defaults for metaprogramming, initialization values, optimization boundaries, and binary search controls.

# Fields

  * `metaprogramming::Bool`: Enables metaprogramming for symbolic calculus conversions. Default is `true`.
  * `μ::Real`: A regularization hyperparameter. Default is `1`.
  * `ϵ::Real`: A regularization hyperparameter. Default is `eps()`.
  * `A_init_value::Real`: Initial value for parameter `A`. Default is `1.0`.
  * `A_lower::Union{Real, Nothing}`: Lower bound for `A`, or `nothing`. Default is `nothing`.
  * `A_upper::Union{Real, Nothing}`: Upper bound for `A`, or `nothing`. Default is `nothing`.
  * `A_use_sobol::Bool`: Use Sobol sequences for initializing `A`. Default is `false`.
  * `V_init_value::Real`: Initial value for parameter `V`. Default is `1.0`.
  * `V_lower::Union{Real, Nothing}`: Lower bound for `V`, or `nothing`. Default is `nothing`.
  * `V_upper::Union{Real, Nothing}`: Upper bound for `V`, or `nothing`. Default is `nothing`.
  * `V_use_sobol::Bool`: Use Sobol sequences for initializing `V`. Default is `false`.
  * `low::Real`: Lower bound for binary search. Default is `-1e10`.
  * `high::Real`: Upper bound for binary search. Default is `1e10`.
  * `tol::Real`: Tolerance for stopping binary search. Default is `1e-10`.
  * `maxiter::Real`: Maximum iterations for binary search. Default is `1e6`.

!!! info
    The `metaprogramming` flag controls whether metaprogramming is used during symbolic differentiation conversion. While conversion between Symbolics.jl atoms and base Julia can occur without it, this approach is slower and requires more calls. Nonetheless, the flag is provided for users who keenly want to avoid metaprogramming in their pipeline.

