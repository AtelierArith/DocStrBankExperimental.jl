```
Cut
```

Contains data for a Ticra "Tabulated Pattern Data" object. Note that a single `Cut` instance  contains all of the cuts for a single frequency.

### Fields

  * `ncomp::Int`: Number of polarization components (2 or 3)
  * `icut::Int`: 1 for standard constant ϕ polar cuts, 2 for conical, constant θ cuts.
  * `icomp::Int`: Polarization control parameter. 1 for Eθ and Eφ, 2 for RHCP and LHCP, 3 for Co and Cx (Ludwig 3).
  * `text::Vector{String}`: Identification text for each constant angle cut.
  * `theta::Tt<:AbstractRange`: The theta values (in degrees) stored in the cut.
  * `phi::Tp<:AbstractRange`: The phi values (in degrees) stored in the cut.
  * `evec`: Matrix of complex field vectors for the two or three polarization components.
