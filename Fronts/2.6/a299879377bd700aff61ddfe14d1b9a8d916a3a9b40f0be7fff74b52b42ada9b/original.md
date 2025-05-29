```
CauchyProblem(eq::DiffusionEquation; b, d_dob[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
CauchyProblem(D; b, d_dob[, ob]) <: AbstractSemiinfiniteProblem{DiffusionEquation{1}}
```

Semi-infinite problem with a Cauchy boundary condition (and unknown initial condition).

# Arguments

  * `eq`: governing equation.
  * `D`: diffusivity function. Shortcut for `CauchyProblem(DiffusionEquation(D), ...)`.

# Keyword arguments

  * `b`: imposed boundary value.
  * `d_dob`: imposed value of the `o`-derivative of the solution at the boundary, where `o` is the Boltzmann variable.

This value is equivalent to `√t*d_dr(<solution>, :b, t)` at any time `t>0`.

  * `ob=0`: boundary constant for an optional moving boundary. At time `t`, the boundary is located at `ob*√t`. Must be positive if `eq` is radial.

# Examples

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> prob = Fronts.CauchyProblem(D, b=2, d_dob=-0.1)
⎧ ∂u/∂t = ∂(D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(0,t) = 2, t>0
⎩ √t*∂u/∂r(0,t) = -0.1, t>0
```

See also: [`DiffusionEquation`](@ref)
