```julia
struct SectionPS{Tn, Tc, Tnb, Tcb, Tr} <: BifurcationKit.AbstractSection
```

This composite type (named for SectionPoincaréShooting) encodes a type of Poincaré sections implemented by hyperplanes. It can be used in conjunction with [`PoincareShootingProblem`](@ref). Each hyperplane is defined par a point (one example in `centers`) and a normal (one example in `normals`).

  * `M::Int64`
  * `normals::Any`
  * `centers::Any`
  * `indices::Vector{Int64}`
  * `normals_bar::Any`
  * `centers_bar::Any`
  * `radius::Any`

# Constructor(s)

```
SectionPS(normals, centers)
```
