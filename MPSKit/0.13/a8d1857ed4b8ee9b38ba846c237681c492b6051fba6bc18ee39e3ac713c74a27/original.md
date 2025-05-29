```julia
struct TaylorCluster <: MPSKit.Algorithm
```

Algorithm for constructing the `N`th order time evolution MPO using the Taylor cluster expansion.

## Fields

  * `N::Int64`: order of the Taylor expansion
  * `extension::Bool`: include higher-order corrections
  * `compression::Bool`: approximate compression of corrections, accurate up to order `N`

## References

  * [Van Damme et al. SciPost Phys. 17 (2024)](@cite vandamme2024)
