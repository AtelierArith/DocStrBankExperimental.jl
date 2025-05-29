```
Metabolite(name::String, commonname::Union{Missing, String}, mz::Union{Missing, Float64}, rt::Union{Missing, Float64}) <: AbstractFeature
Metabolite(name::String)
```

Represents a small-molecule metabolite coming from an LCMS. The fields are

  * `name`: required, this should be a unique identifier
  * `commonname`: might refer to a chemical name like "proprionate"
  * `mz`: The mass/charge ratio
  * `rt`: The retention time
