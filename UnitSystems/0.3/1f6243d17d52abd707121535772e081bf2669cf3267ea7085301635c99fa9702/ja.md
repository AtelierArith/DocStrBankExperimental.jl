```Julia
Rydberg = UnitSystem(𝟏,𝟏,𝟐/α,τ/𝟐*α^2,𝟏/𝟐)
```

Rydberg `UnitSystem` の `lightspeed` は `𝟐/α` で、`permeability` は `π*α^2` です。

```Julia
julia> boltzmann(Rydberg)
1

julia> planckreduced(Rydberg)
1

julia> lightspeed(Rydberg)
274.071998168

julia> vacuumpermeability(Rydberg)
0.00016729406415509762

julia> electronmass(Rydberg)
0.5
```

よく知られている `Rydberg` 原子単位の値は、`length`、`time`、`mass`、および `charge` について次の通りです：

```Julia
julia> length(Rydberg,SI2019) # lR
5.291772109022829e-11

julia> time(Rydberg,SI2019) # tR
4.837768653171316e-17

julia> mass(Rydberg,SI2019) # mR
1.8218767403116513e-30

julia> charge(Rydberg,SI2019) # qR
1.1329099625600374e-19
```
