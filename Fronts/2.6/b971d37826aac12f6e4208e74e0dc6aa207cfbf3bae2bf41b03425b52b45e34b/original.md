```
DirichletProblem(eq::DiffusionEquation; i, b[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
DirichletProblem(D; i, b[, ob]) <: AbstractSemiinfiniteProblem{DiffusionEquation{1}}
```

Semi-infinite problem with a Dirichlet boundary condition.

# Arguments

  * `eq`: governing equation.
  * `D`: diffusivity function. Shortcut for `DirichletProblem(DiffusionEquation(D), ...)`.

# Keyword arguments

  * `i`: initial value.
  * `b`: imposed boundary value.
  * `ob=0`: boundary constant for an optional moving boundary. At time `t`, the boundary is located at `ob*√t`. Must be positive if `eq` is radial.

# Examples

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> prob = Fronts.DirichletProblem(D, i=1, b=2)
⎧ ∂u/∂t = ∂(D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(r,0) = 1, r>0
⎩ u(0,t) = 2, t>0
```

See also: [`DiffusionEquation`](@ref)
