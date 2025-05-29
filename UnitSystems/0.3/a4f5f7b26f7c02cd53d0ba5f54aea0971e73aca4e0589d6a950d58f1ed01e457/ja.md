```Julia
NaturalGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,𝟏)
```

自然（ガウス）`UnitSystem` は、ガウスの`permeability`値が`4π`です。

```Julia
julia> boltzmann(NaturalGauss)
1

julia> planckreduced(NaturalGauss)
1

julia> lightspeed(NaturalGauss)
1

julia> vacuumpermeability(NaturalGauss)
12.566370614359172

julia> electronmass(NaturalGauss)
1
```
