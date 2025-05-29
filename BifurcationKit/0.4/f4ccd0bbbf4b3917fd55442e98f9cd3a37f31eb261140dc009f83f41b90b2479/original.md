```julia
struct PALC{Ttang<:BifurcationKit.AbstractTangentComputation, Tbls<:BifurcationKit.AbstractLinearSolver, T, Tdot} <: BifurcationKit.AbstractContinuationAlgorithm
```

Pseudo-arclength continuation algorithm.

Additional information is available on the [website](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/PALC/).

# Fields

  * `tangent::BifurcationKit.AbstractTangentComputation`: Tangent predictor, must be a subtype of `AbstractTangentComputation`. For example `Secant()` or `Bordered()`,  Default: Secant()
  * `θ::Any`: `θ` is a parameter in the arclength constraint. It is very **important** to tune it. It should be tuned for the continuation to work properly especially in the case of large problems where the < x - x*0, dx*0 > component in the constraint equation might be favoured too much. Also, large thetas favour p as the corresponding term in N involves the term 1-theta. Default: 0.5
  * `_bothside::Bool`: [internal],  Default: false
  * `bls::BifurcationKit.AbstractLinearSolver`: Bordered linear solver used to invert the jacobian of the bordered problem during newton iterations. It is also used to compute the tangent for the predictor `Bordered()`,  Default: MatrixBLS()
  * `dotθ::Any`: `dotθ = DotTheta()`, this sets up a dot product `(x, y) -> dot(x, y) / length(x)` used to define the weighted dot product (resp. norm) $\|(x, p)\|^2_\theta$ in the constraint $N(x, p)$ (see online docs on [PALC](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/PALC/)). This argument can be used to remove the factor `1/length(x)` for example in problems where the dimension of the state space changes (mesh adaptation, ...) or when a specific (FEM) dot product is provided. Default: DotTheta()
