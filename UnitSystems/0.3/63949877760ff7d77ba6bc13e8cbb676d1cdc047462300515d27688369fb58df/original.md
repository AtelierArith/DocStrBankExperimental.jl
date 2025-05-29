```Julia
electronradius(U::UnitSystem) = finestructure(U)*planckreduced(U)*gravity(U)/electronmass(U)/lightspeed(U)
```

Classical electron radius or Lorentz radius or Thomson scattering length (m).

```Julia
julia> electronradius(Metric) # m
2.8179403261891358e-15

julia> electronradius(CODATA) # m
2.8179403261891366e-15

julia> electronradius(Conventional) # m
2.817940326189136e-15

julia> electronradius(Hartree) # a₀
5.3251354520432896e-5
```
