```Julia
Stoney = UnitSystem(𝟏,𝟏/α,𝟏,𝟐*τ,√(αG/α))
```

Stoney `UnitSystem` の `permeability` は `4π` で、`electronmass` の結合は `√(αG/α)` です。

```Julia
julia> boltzmann(Stoney)
1

julia> planckreduced(Stoney)
137.035999084

julia> lightspeed(Stoney)
1

julia> vacuumpermeability(Stoney)
12.566370614359172

julia> electronmass(Stoney)
4.899602291219254e-22
```

よく知られた `Stoney` の値は、`length`、`time`、`mass`、および `charge` です。

```Julia
julia> length(Stoney,SI2019) # lS
1.380678687871542e-36

julia> time(Stoney,SI2019) # tS
4.605448372792427e-45

julia> mass(Stoney,SI2019) # mS
1.859208801066057e-9

julia> charge(Stoney,SI2019) # qS
1.602176634e-19
```
