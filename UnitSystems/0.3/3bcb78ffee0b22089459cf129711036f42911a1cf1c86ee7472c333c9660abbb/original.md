```Julia
Meridian = EntropySystem(Metric,𝟏,em,em^3,𝟏,τ/𝟐^6/𝟓^7,milli)
```

Modern ideal `Meridian` system defined by France's original `earthmeter` definition.

```Julia
julia> greatcircle(Meridian) # em
4.000000000000001e7

julia> boltzmann(Meridian) # eJ⋅K⁻¹
1.3706960050349812e-23

julia> planckreduced(Meridian) # eJ⋅s⋅rad⁻¹
1.0469694889627603e-34

julia> lightspeed(Meridian) # em⋅s⁻¹
2.9935896995513964e8

julia> vacuumpermeability(Meridian) # kegf⋅s²⋅eC⁻²
1.2566370614359173e-6

julia> electronmass(Meridian) # keg
9.06992538542115e-31

julia> molarmass(Meridian) # keg⋅eg-mol⁻¹
0.001

julia> luminousefficacy(Meridian) # lm⋅W⁻¹
687.979280828919
```
