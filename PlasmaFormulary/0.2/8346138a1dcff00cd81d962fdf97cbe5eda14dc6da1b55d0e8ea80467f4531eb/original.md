Calculate the radius of circular motion for a charged particle in a uniform magnetic field

References: [PlasmaPy API Documentation](https://docs.plasmapy.org/en/latest/api/plasmapy.formulary.lengths.gyroradius.html)

# Examples

```jldoctest
julia> gyroradius(0.2u"T", Unitful.me, Unitful.q, 1e6u"K")
0.00015651672339994665 m
```
