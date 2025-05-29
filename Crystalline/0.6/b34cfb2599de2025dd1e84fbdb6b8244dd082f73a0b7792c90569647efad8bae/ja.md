```julia
struct LGIrrep{D} <: Crystalline.AbstractIrrep{D}
```

  * `cdml::String`
  * `g::Crystalline.LittleGroup`
  * `matrices::Vector{Matrix{ComplexF64}}`
  * `translations::Vector{Vector{Float64}}`
  * `reality::Crystalline.Reality`
  * `iscorep::Bool`
