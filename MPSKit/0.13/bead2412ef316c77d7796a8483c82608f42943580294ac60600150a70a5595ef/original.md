```julia
struct GradientGrassmann{O<:OptimKit.OptimizationAlgorithm, F} <: MPSKit.Algorithm
```

Variational gradient-based optimization algorithm that keeps the MPS in left-canonical form, as points on a Grassmann manifold. The optimization is then a Riemannian gradient descent  with a preconditioner to induce the metric from the Hilbert space inner product.

## Fields

  * `method::OptimKit.OptimizationAlgorithm`: optimization algorithm
  * `finalize!::Any`: callback function applied after each iteration, of signature `finalize!(x, f, g, numiter) -> x, f, g`

## References

  * [Hauru et al. SciPost Phys. 10 (2021)](@cite hauru2021)

---

## Constructors

```
GradientGrassmann(; kwargs...)
```

### Keywords

  * `method=ConjugateGradient`: instance of optimization algorithm, or type of optimization   algorithm to construct
  * `finalize!`: finalizer algorithm
  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int`: maximum amount of iterations
  * `verbosity::Int`: level of information display
