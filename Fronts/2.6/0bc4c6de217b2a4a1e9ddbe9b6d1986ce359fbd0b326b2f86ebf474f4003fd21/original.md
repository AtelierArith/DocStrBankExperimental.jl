```
SorptivityProblem(eq::DiffusionEquation; i, S[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
SorptivityProblem(D; i, S[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
```

Semi-infinite problem with a known initial condition and soprtivity.

# Arguments

  * `eq`: governing equation.
  * `D`: diffusivity function. Shortcut for `SorptivityProblem(DiffusionEquation(D), ...)`.

# Keyword arguments

  * `i`: initial value.
  * `S`: prescribed sorptivity.
  * `ob=0`: boundary constant for an optional moving boundary. At time `t`, the boundary is located at `ob*√t`. Must be positive if `eq` is radial.

# Examples

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> prob = Fronts.SorptivityProblem(D, i=0, S=1)
⎧ ∂u/∂t = ∂(D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(r,0) = 0, r>0
⎩ S = 1
```

See also: [`DiffusionEquation`](@ref), [`sorptivity`](@ref)
