```
SorptivityCauchyProblem(eq::DiffusionEquation; b, S[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
SorptivityCauchyProblem(D; b, S[, ob]) <: AbstractSemiiinfiniteProblem{DiffusionEquation{1}}
```

Semi-infinite problem with a known boundary value and soprtivity (and unknown initial condition).

# Arguments

  * `eq`: governing equation.
  * `D`: diffusivity function. Shortcut for `SorptivityCauchyProblem(DiffusionEquation(D), ...)`.

# Keyword arguments

  * `b`: imposed boundary value.
  * `S`: prescribed sorptivity.
  * `ob=0`: boundary constant for an optional moving boundary. At time `t`, the boundary is located at `ob*√t`. Must be positive if `eq` is radial.

# Examples

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> prob = Fronts.SorptivityCauchyProblem(D, b=2, S=1)
⎧ ∂u/∂t = ∂(D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(0,t) = 2, t>0
⎩ S = 1
```

See also: [`DiffusionEquation`](@ref), [`sorptivity`](@ref)
