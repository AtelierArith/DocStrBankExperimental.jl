```
FlowrateProblem(eq::DiffusionEquation{2}; i, Qb[, angle, height, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
```

Semi-infinite radial (polar/cylindrical) problem with an imposed-flowrate boundary condition.

# Arguments

  * `eq`: governing equation.

# Keyword arguments

  * `i`: initial value.
  * `Qb`: imposed boundary flowrate.
  * `angle=2π`: total angle covered by the domain.
  * `height=1`: domain height.
  * `ob=0`: boundary constant for an optional moving boundary. At time `t`, the boundary is located at `ob*√t`.

# Examples

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> eq = Fronts.DiffusionEquation{2}(D)
∂u/∂t = 1/r*∂(r*D(u)*∂u/∂r)/∂r

julia> prob = Fronts.FlowrateProblem(eq, i=1, Qb=1)
⎧ ∂u/∂t = 1/r*∂(r*D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(r,0) = 1, r>0
⎩ Qb(0,t) = 1, t>0
```

See also: [`DiffusionEquation`](@ref)
