```julia
struct SectionSS{Tn} <: BifurcationKit.AbstractSection
```

This composite type (named for Section Standard Shooting) encodes a type of section implemented by a single hyperplane. It can be used in conjunction with [`ShootingProblem`](@ref). The hyperplane is defined by a point `center` and a `normal`.

  * `normal::Any`: Normal to define hyperplane
  * `center::Any`: Representative point on hyperplane
