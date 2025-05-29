```julia
alternate_field_names()

```

Returns a `NamedTuple` of mappings between alternate ascii field names and field names with special characters. These can be used when indexing `Solution` objects instead of the short names.

# Usage

```jldoctest; setup = :(using HallThruster)
julia> HallThruster.alternate_field_names()
(mobility = :μ, potential = :ϕ, thermal_conductivity = :κ, grad_pe = :∇pe, nu_anom = :νan, nu_class = :νc, nu_wall = :νew_momentum, nu_ei = :νei, nu_en = :νen, nu_iz = :νiz, nu_ex = :νex, tan_divergence_angle = :tanδ)
```
