```julia
struct IterSVD
```

Iterative SVD solver based on KrylovKit's GKL algorithm, adapted to (symmetric) tensors. The number of targeted singular values is set via the `TruncationSpace` in `ProjectorAlg`. In particular, this make it possible to specify the targeted singular values block-wise. In case the symmetry block is too small as compared to the number of singular values, or the iterative SVD didn't converge, the algorithm falls back to a dense SVD.

## Fields

  * `alg::KrylovKit.GKL`
  * `fallback_threshold::Float64`
  * `start_vector::Any`

## Constructors

```
IterSVD(; kwargs...)
```

Construct an `IterSVD` algorithm struct based on the following keyword arguments:

  * `alg::KrylovKit.GKL=KrylovKit.GKL(; tol=1e-14, krylovdim=25)` : GKL algorithm struct for block-wise iterative SVD.
  * `fallback_threshold::Float64=Inf` : Threshold for `howmany / minimum(size(block))` above which (if the block is too small) the algorithm falls back to TensorKit's dense SVD.
  * `start_vector=random_start_vector` : Function providing the initial vector for the iterative SVD algorithm.
