```julia
struct PeriodicOrbitOCollProblem{Tprob<:Union{Nothing, BifurcationKit.AbstractBifurcationProblem}, Tjac<:BifurcationKit.AbstractJacobianType, 𝒯, vectype, ∂vectype, Tmass} <: BifurcationKit.AbstractPODiffProblem
```

This composite type implements an orthogonal collocation (at Gauss points) method of piecewise polynomials to locate periodic orbits. More details (maths, notations, linear systems) can be found [here](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitCollocation/).

## Fields

  * `prob_vf::Union{Nothing, BifurcationKit.AbstractBifurcationProblem}`: `prob` a bifurcation problem Default: nothing
  * `ϕ::Any`: used to set a section for the phase constraint equation Default: nothing
  * `xπ::Any`: used in the section for the phase constraint equation Default: nothing
  * `∂ϕ::Any`: we store the derivative of ϕ, no need to recompute it each time. Default: nothing
  * `N::Int64`: dimension of the state space Default: 0
  * `isautonomous::Bool`: Default: true
  * `massmatrix::Any`: Default: nothing
  * `update_section_every_step::UInt64`: updates the section every `update_section_every_step` step during continuation Default: 1
  * `jacobian::BifurcationKit.AbstractJacobianType`: describes the type of jacobian used in Newton iterations. Can only be `AutoDiffDense(), DenseAnalytical(), FullSparse(), FullSparseInplace(), DenseAnalyticalInplace()`. Default: DenseAnalytical()
  * `mesh_cache::BifurcationKit.MeshCollocationCache`: cache for collocation. See docs of `MeshCollocationCache` Default: nothing
  * `cache::BifurcationKit.POCollCache`: Default: nothing
  * `meshadapt::Bool`: whether to use mesh adaptation Default: false
  * `verbose_mesh_adapt::Bool`: Default: false
  * `K::Float64`: parameter for mesh adaptation, control new mesh step size. More precisely, we set max(hᵢ) / min(hᵢ) ≤ K if hᵢ denotes the time steps. Default: 100

## Methods

Here are some useful methods you can apply to `pb`

  * `length(pb)` gives the total number of unknowns
  * `size(pb)` returns the triplet `(N, m, Ntst)`
  * `getmesh(pb)` returns the mesh `0 = τ₀ < ... < τₙₜₛₜ₊₁ = 1`. This is useful because this mesh is born to vary during automatic mesh adaptation
  * `get_mesh_coll(pb)` returns the (static) mesh `0 = σ₀ < ... < σₘ₊₁ = 1`
  * `get_times(pb)` returns the vector of times (length `1 + m * Ntst`) at the which the collocation is applied.
  * `generate_solution(pb, orbit, period)` generate a guess from a function `t -> orbit(t)` which approximates the periodic orbit.
  * `POSolution(pb, x)` return a function interpolating the solution `x` using a piecewise polynomials function

# Orbit guess

You can evaluate the residual of the functional (and other things) by calling `pb(orbitguess, p)` on an orbit guess `orbitguess`. Note that `orbitguess` must be of size 1 + N * (1 + m * Ntst) where N is the number of unknowns in the state space and `orbitguess[end]` is an estimate of the period $T$ of the limit cycle.

Note that you can generate this guess from a function using `generate_solution` or `generate_ci_problem`.

# Constructors

  * `PeriodicOrbitOCollProblem(Ntst::Int, m::Int; kwargs)` creates an empty functional with `Ntst` and `m`.

# Functional

A functional, hereby called `G`, encodes this problem. The following methods are available

  * `residual(pb, orbitguess, p)` evaluates the functional G on `orbitguess`
  * `residual!(pb, out, orbitguess, p)` evaluates the functional G on `orbitguess`
