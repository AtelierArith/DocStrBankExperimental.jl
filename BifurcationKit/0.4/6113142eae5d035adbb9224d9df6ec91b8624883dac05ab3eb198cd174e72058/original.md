```julia
struct DeflationOperator{Tp<:Real, Tdot, T<:Real, vectype} <: BifurcationKit.AbstractDeflationFactor
```

Structure for defining a custom distance.

This operator allows to handle the following situation. Assume you want to solve `F(x)=0` with a Newton algorithm but you want to avoid the process to return some already known solutions $roots_i$. The deflation operator penalizes these roots. You can create a `DeflationOperator` to define a scalar function `M(u)` used to find, with Newton iterations, the zeros of the following function $F(u) \cdot Π_i(\|u - root_i\|^{-2p} + \alpha) := F(u) \cdot M(u)$ where $\|u\|^2 = dot(u, u)$. The fields of the struct `DeflationOperator` are as follows:

  * `power::Real`: power `p`. You can use an `Int` for example
  * `dot::Any`: function, this function has to be bilinear and symmetric for the linear solver to work well
  * `α::Real`: shift
  * `roots::Vector`: roots
  * `tmp::Any`
  * `autodiff::Bool`
  * `δ::Real`

Given `defOp::DeflationOperator`, one can access its roots via `defOp[n]` as a shortcut for `defOp.roots[n]`. Note that you can also use `defOp[end]`.

Also, one can add (resp. remove) a new root by using `push!(defOp, newroot)` (resp. `pop!(defOp)`). Finally `length(defOp)` is a shortcut for `length(defOp.roots)`

## Constructors

  * `DeflationOperator(p::Real, α::Real, roots::Vector{vectype}; autodiff = false)`
  * `DeflationOperator(p::Real, dt, α::Real, roots::Vector{vectype}; autodiff = false)`
  * `DeflationOperator(p::Real, α::Real, roots::Vector{vectype}, v::vectype; autodiff = false)`

The option `autodiff` triggers the use of automatic differentiation for the computation of the gradient of the scalar function `M`. This works only on `AbstractVector` for now.

## Custom distance

You are asked to pass a scalar product like `dot` to build a `DeflationOperator`. However, in some cases, you may want to pass a custom distance `dist(u, v)`. You can do this using

```
`DeflationOperator(p, CustomDist(dist), α, roots)`
```

Note that passing `CustomDist(dist, true)` will trigger the use of automatic differentiation for the gradient of `M`.

## Linear solvers

When used with newton, you have access to the following linear solvers

  * custom solver `DeflatedProblemCustomLS()` which requires solving two linear systems `J⋅x = rhs`.
  * For other linear solvers `<: AbstractLinearSolver`, a matrix free method is used for the deflated functional.
  * if passed `Val(:autodiff)`, then `ForwardDiff.jl` is used to compute the jacobian Matrix of the deflated problem
  * if passed `Val(:fullIterative)`, then a full matrix free method is used for the deflated problem.
