```julia
struct SDDDEBifProblem{Tvf, Tdf, Tu, Td, Tp, Tl<:Union{typeof(identity), Nothing, Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}, Tplot, Trec, Tgets, Tδ} <: DDEBifurcationKit.AbstractDDEBifurcationProblem
```

Structure to hold the bifurcation problem. If don't have parameters, you can pass `nothing`.

## Fields

  * `VF::Any`: Vector field, typically a [`BifFunction`](@ref). For more information, please look at the website https://bifurcationkit.github.io/DDEBifurcationKit.jl/dev/BifProblem
  * `delays::Any`: function delays. It takes the parameters and the state and return the non-zero delays in an `AsbtractVector` form. Example: `delays = (par, u) -> [1. + u[1]^2]`
  * `u0::Any`: Initial guess
  * `delays0::Any`: initial delays (set internally by the constructor)
  * `params::Any`: parameters
  * `lens::Union{typeof(identity), Nothing, Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}`: see ConstantDDEBifProblem for more information.
  * `plotSolution::Any`: user function to plot solutions during continuation. Signature: `plotSolution(x, p; kwargs...)`
  * `recordFromSolution::Any`: `record_from_solution = (x, p; k...) -> norm(x)` function used record a few indicators about the solution. It could be `norm` or `(x, p) -> x[1]`. This is also useful when saving several huge vectors is not possible for memory reasons (for example on GPU...). This function can return pretty much everything but you should keep it small. For example, you can do `(x, p) -> (x1 = x[1], x2 = x[2], nrm = norm(x))` or simply `(x, p) -> (sum(x), 1)`. This will be stored in `contres.branch` (see below). Finally, the first component is used to plot in the continuation curve.
  * `save_solution::Any`: function to save the full solution on the branch. Some problem are mutable (like periodic orbit functional with adaptive mesh) and this function allows to save the state of the problem along with the solution itself. Signature `save_solution(x, p)`
  * `δ::Any`: delta for Finite differences

## Methods

  * `getu0(pb)` calls `pb.u0`
  * `getparams(pb)` calls `pb.params`
  * `getlens(pb)` calls `pb.lens`
  * `setparam(pb, p0)` calls `set(pb.params, pb.lens, p0)`
  * `record_from_solution(pb)` calls `pb.record_from_solution`

## Constructors

  * `SDDDEBifProblem(F, delays, u0, params, lens; J, Jᵗ, d2F, d3F, kwargs...)` and `kwargs` are the fields above.
