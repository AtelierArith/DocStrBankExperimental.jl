```
@liquid name temp dens visc surftens pv Ev
```

Create a liquid of the specified name, with viscosity `visc`, surface tension `surftens`, vapor pressure `pv`, and bulk modulus `Ev` at reference temperature `temp`. Each of these must be provided with units if they are not the default.

# Example

```jldoctest myliq
julia> @liquid MyWater 15u"°C" 999 1.13e-3 7.34e-2 1.77e3 2.15e9

julia> MyWater
Liquid with
   Density = 999.0 kg m⁻³
   Viscosity = 0.00113 kg m⁻¹ s⁻¹
   Kinematic viscosity = 1.131131131131131e-6 m² s⁻¹
   Specific weight = 9796.84335 N m⁻³
   Surface tension = 0.0734 N m⁻¹
   Bulk modulus = 2.15e9 Pa
   Vapor pressure = 1770.0 Pa
   at reference temp 288.15 K
```
