```
@gas name temp visc gamma mmass
```

Create a gas of the specified name, with viscosity `visc` and ratio of specific heats `gamma` at reference temperature `temp`, and molar mass `mmass`. Each of these must be provided with units if they are not the default.

# Example

```jldoctest mygas
julia> @gas MyO2 20u"°C" 2.04e-5 1.395 31.999u"g/mol"

julia> MyO2
Perfect gas with
   Density = 1.330236729981785 kg m⁻³
   Viscosity = 2.04e-5 kg m⁻¹ s⁻¹
   Specific heat ratio = 1.395
   Gas constant = 259.83507666343445 J kg⁻¹ K⁻¹
   cp = 917.645397330357 J kg⁻¹ K⁻¹
   cv = 657.8103206669226 J kg⁻¹ K⁻¹
   at reference temp 293.15 K
```
