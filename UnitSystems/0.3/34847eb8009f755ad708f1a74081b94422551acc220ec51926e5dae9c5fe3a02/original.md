```Julia
vectorpotential(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)/length(U,S)
vectorpotential(v::Real,U::UnitSystem,S::UnitSystem) = v/vectorpotential(U,S)
```

Magnetic `vectorpotential` or electromagnetic rigidity (Wb⋅m⁻¹ or T⋅m), unit conversion factor.

```julia
julia> vectorpotential(EMU,Metric) # Wb⋅cm⋅Mx⁻¹⋅m⁻¹
9.999999999999997e-7

julia> vectorpotential(ESU,Metric) # Wb⋅cm⋅statWb⁻¹⋅m⁻¹
29979.2458

julia> vectorpotential(Metric,SI2019) # Wb⋅Wb⁻¹
1.0000000002726048
```
