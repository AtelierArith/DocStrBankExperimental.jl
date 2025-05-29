```julia
struct BifurcationProblem{Tvf, Tu, Tp, Tl<:Union{typeof(identity), Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}, Tplot, Trec, Tgets, Tupdate} <: BifurcationKit.AbstractAllJetBifProblem
```

Structure to hold the bifurcation problem.

## Fields

  * `VF::Any`: Vector field, typically a [`BifFunction`](@ref)
  * `u0::Any`: Initial guess
  * `params::Any`: parameters
  * `lens::Union{typeof(identity), Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}`: Typically a `Accessors.PropertyLens`. It specifies which parameter axis among `params` is used for continuation. For example, if `par = (α = 1.0, β = 1)`, we can perform continuation w.r.t. `α` by using `lens = (@optic _.α)`. If you have an array `par = [ 1.0, 2.0]` and want to perform continuation w.r.t. the first variable, you can use `lens = (@optic _[1])`. For more information, we refer to `Accessors.jl`.
  * `plotSolution::Any`: user function to plot solutions during continuation. Signature: `plot_solution(x, p; kwargs...)` for Plot.jl and `plot_solution(ax, x, p; ax1 = nothing, kwargs...)` for the Makie package(s).
  * `recordFromSolution::Any`: `record_from_solution = (x, p; k...) -> norm(x)` function used record a few indicators about the solution. It could be `norm` or `(x, p; k...) -> x[1]`. This is also useful when saving several huge vectors is not possible for memory reasons (for example on GPU). This function can return pretty much everything but you should keep it small. For example, you can do `(x, p; k...) -> (x1 = x[1], x2 = x[2], nrm = norm(x))` or simply `(x, p; k...) -> (sum(x), 1)`. This will be stored in `contres.branch` where `contres::ContResult` is the continuation curve of the bifurcation problem. Finally, the first component is used for plotting in the continuation curve.
  * `save_solution::Any`: function to save the full solution on the branch. Some problem are mutable (like periodic orbit functional with adaptive mesh) and this function allows to save the state of the problem along with the solution itself. Note that this should allocate the output (not as a view to `x`). Signature: `save_solution(x, p)`
  * `update!::Any`: Function used to update the problem after each continuation step

## Methods

  * `re_make(pb; kwargs...)` modify a bifurcation problem
  * `getu0(pb)` calls `pb.u0`
  * `getparams(pb)` calls `pb.params`
  * `getlens(pb)` calls `pb.lens`
  * `getparam(pb)` calls `get(pb.params, pb.lens)`
  * `setparam(pb, p0)` calls `set(pb.params, pb.lens, p0)`
  * `record_from_solution(pb)` calls `pb.recordFromSolution`
  * `plot_solution(pb)` calls `pb.plotSolution`
  * `is_symmetric(pb)` calls `is_symmetric(pb.prob)`

## Constructors

  * `BifurcationProblem(F, u0, params, lens)` all derivatives are computed using ForwardDiff.
  * `BifurcationProblem(F, u0, params, lens; J, Jᵗ, d2F, d3F, kwargs...)` and `kwargs` are the fields above. You can pass your own jacobian with `J` (see [`BifFunction`](@ref) for description of the jacobian function) and jacobian adjoint with `Jᵗ`. For example, this can be used to provide finite differences based jacobian using `BifurcationKit.finite_differences`. You can also pass

      * `record_from_solution` see above
      * `plot_solution` see above
      * `issymmetric[=false]` whether the jacobian is symmetric, this remove the need of providing an adjoint
      * `jvp` jacobian-vector product, signature `jvp(x,p,dx)`
      * `vjp` vector-jacobian product (adjoint of jvp), signature `vjp(x,p,dx)`
      * `d2F` second Differential of `F` with respect to `x`, signature `d2F(x,p,dx1,dx2)`
      * `d3F` third Differential of `F` with respect to `x`, signature `d3F(x,p,dx1,dx2,dx3)`
      * `save_solution` specify a particular way to record solution which are written in `br.sol`. This can be useful in very particular situations and we recommend using `record_from_solution` instead. For example, it is used internally to record the mesh in the collocation method because this mesh can be modified.
