```
dimensionOf(abstractUnit::AbstractUnit)
```

Returns the dimension of a physical unit of type [`AbstractUnit`](@ref).

# Example

One siemens is defined as $1\,\mathrm{S} = 1\,\mathrm{kg}^{-1}\,\mathrm{m}^{-2}\,\mathrm{s}^3\,\mathrm{A}^2$. The unit is hence of dimension $\mathrm{M}^{-1}\,\mathrm{L}^{-2}\,\mathrm{T}^3\,\mathrm{I}^2$:

```jldoctest
julia> ucat = UnitCatalogue() ;

julia> siemens = ucat.siemens
BaseUnit siemens (1 S = 1 kg^-1 m^-2 s^3 A^2)
julia> dimensionOf(siemens)
Dimension M^-1 L^-2 T^3 I^2
```
