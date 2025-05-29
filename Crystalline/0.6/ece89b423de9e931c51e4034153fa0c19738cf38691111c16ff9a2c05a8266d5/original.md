```julia
struct PGIrrep{D} <: Crystalline.AbstractIrrep{D}
```

  * `cdml::String`
  * `g::Crystalline.PointGroup`
  * `matrices::Vector{Matrix{ComplexF64}}`
  * `reality::Crystalline.Reality`
  * `iscorep::Bool`
