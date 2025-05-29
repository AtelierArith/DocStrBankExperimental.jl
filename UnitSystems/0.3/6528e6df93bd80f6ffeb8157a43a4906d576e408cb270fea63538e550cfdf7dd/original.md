```Julia
FPS = RankineSystem(Metric,ft,lb)
```

Absolute English `UnitSystem` based on the foot, pound, second, and poundal.

```Julia
julia> boltzmann(FPS) # ft⋅pdl⋅°R⁻¹
1.8201832416933465e-22

julia> planckreduced(FPS) # ft⋅pdl⋅s⋅rad⁻¹
2.502536930488925e-33

julia> lightspeed(FPS) # ft⋅s⁻¹
9.835710564304461e8

julia> vacuumpermeability(FPS) # lb⋅ft⋅C⁻²
9.089273271309687e-6

julia> electronmass(FPS) # lb
2.0082753379555867e-30

julia> molarmass(FPS) # lb⋅lb-mol⁻¹
1

julia> luminousefficacy(FPS) # lm⋅s³⋅lb⁻¹⋅ft⁻²
28.78252493663283
```
