```
TrustRegion
```

Functor object for using trust-region regularization in an L-shaped algorithm. Create by supplying a [`TR`](@ref) object through `regularize` in `LShaped.Optimizer` or by setting the [`Regularizer`](@ref) attribute.

...

# Parameters

  * `γ::T = 1e-4`: Relative tolerance for deciding if a minor iterate should be accepted as a new major iterate.
  * `Δ::AbstractFloat = 1.0`: Initial size of ∞-norm trust-region.
  * `Δ̅::AbstractFloat = 1000.0`: Maximum size of ∞-norm trust-region.

...
