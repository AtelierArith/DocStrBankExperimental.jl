```Julia
darcy(U::UnitSystem) = area(milli/atm,U,Gauss)
```

Metric unit of permeability (m² or ft²).

```Julia
julia> darcy(Metric) # m²
9.869232667160132e-13

julia> darcy(CGS) # cm²
9.86923266716013e-9

julia> darcy(English) # ft²
1.062315363109768e-11
```
