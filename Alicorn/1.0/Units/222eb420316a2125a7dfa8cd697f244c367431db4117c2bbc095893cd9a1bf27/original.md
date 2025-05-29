```
convertToUnit(baseUnitExponents::BaseUnitExponents)
```

Return the `Unit` corresponding to a `BaseUnitExponents` object.

# Example

```jldoctest
julia> jouleExponents = BaseUnitExponents(kg=1, m=2, s=-2)
BaseUnitExponents kg^1 m^2 s^-2 A^0 K^0 mol^0 cd^0

julia> convertToUnit(jouleExponents)
Unit kg m^2 s^-2
```
