```julia
struct OptimalExpand{S} <: MPSKit.Algorithm
```

An algorithm that expands the given mps as described in [Zauner-Stauber et al. Phys. Rev. B 97 (2018)](@cite zauner-stauber2018), by selecting the dominant contributions of a two-site updated MPS tensor, orthogonal to the original ψ.

## Fields

  * `alg_svd::Any`: algorithm used for the singular value decomposition
  * `trscheme::TensorKit.TruncationScheme`: algorithm used for truncating the expanded space
