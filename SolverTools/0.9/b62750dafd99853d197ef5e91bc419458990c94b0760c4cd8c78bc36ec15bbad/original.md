```
TrustRegion{T, V} <: AbstractTrustRegion{T, V}
```

Basic trust region type that contains the following fields:

  * `initial_radius::T`: initial radius;
  * `radius::T`: current radius;
  * `max_radius::T`: upper bound on the radius (default `1 / sqrt(eps(T))`);
  * `acceptance_threshold::T`: decrease radius if ratio is below this threshold between 0 and 1 (default `1e-4`);
  * `increase_threshold::T`: increase radius if ratio is beyond this threshold between 0 and 1  (default `0.95`);
  * `decrease_factor::T`: decrease factor less between 0 and 1 (default `1 / 3`);
  * `increase_factor::T`: increase factor greater than one (default `3 / 2`);
  * `ratio::T`: current ratio `ared / pred`;
  * `gt::V`: pre-allocated memory vector to store the gradient of the objective function;
  * `good_grad::Bool`: `true` if `gt` is the gradient of the objective function at the trial point.

The following constructors are available:

```
TrustRegion(gt,::V initial_radius::T; kwargs...)
```

If `gt` is not known, it is possible to use the following constructors:

```
TrustRegion(::Type{V}, n::Int, Δ₀::T; kwargs...)
TrustRegion(n::Int, Δ₀::T; kwargs...)
```

that will allocate a vector of size `n` and type `V` or `Vector{T}`.
