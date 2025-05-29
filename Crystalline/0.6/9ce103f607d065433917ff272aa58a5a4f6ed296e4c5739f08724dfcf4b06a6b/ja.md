```julia
struct SiteIrrep{D} <: Crystalline.AbstractIrrep{D}
```

  * `cdml::String`
  * `g::Crystalline.SiteGroup`
  * `matrices::Vector{Matrix{ComplexF64}}`
  * `reality::Crystalline.Reality`
  * `iscorep::Bool`
  * `pglabel::String`
