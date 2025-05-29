```Julia
IAUJ = EntropySystem(Metric,DAY,JD,GMJ/G)
```

天文学的（木星）`UnitSystem`は、`solarmass`の周りの`jupiterdistance`によって定義されています。

```Julia
julia> boltzmann(IAUJ) # MJ⋅JD²⋅D⁻²
8.959677342845726e-65

julia> planckreduced(IAUJ) # MJ⋅JD²⋅D⁻¹⋅rad⁻¹
7.9208448414543e-81

julia> lightspeed(IAUJ) # JD⋅D⁻¹
33.27266165330086

julia> vacuumpermeability(IAUJ) # MJ⋅JD²⋅C⁻²
8.50429600927554e-46

julia> electronmass(IAUJ) # MJ
4.7991508542640076e-58

julia> molarmass(IAUJ) # MJ⋅mol⁻¹
5.268359541648314e-31

julia> luminousefficacy(IAUJ) # lm⋅D³⋅MJ⁻¹⋅JD⁻²
1.2181769949820595e39

julia> sqrt(gravitation(IAUJ)*solarmass(IAUJ)/jupiterdistance(IAUJ)^3) # D⁻¹
0.001449102839404571
```
