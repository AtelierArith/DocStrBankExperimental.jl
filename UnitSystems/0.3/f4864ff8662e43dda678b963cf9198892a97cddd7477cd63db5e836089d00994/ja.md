```Julia
Natural = UnitSystem(𝟏,𝟏,𝟏,𝟏,𝟏)
```

すべての基本定数が単位値を持つ `UnitSystem` の自然単位系。

```Julia
julia> boltzmann(Natural)
1

julia> planckreduced(Natural)
1

julia> lightspeed(Natural)
1

julia> vacuumpermeability(Natural)
1

julia> electronmass(Natural)
1
```

よく知られている `Natural` の値は、`length`、`time`、`mass`、および `charge` について次の通りです。

```Julia
julia> length(Natural,SI2019)
3.8615926795842105e-13

julia> time(Natural,SI2019)
1.2880886681893147e-21

julia> mass(Natural,SI2019)
9.109383701558256e-31

julia> charge(Natural,SI2019)
5.290817689895691e-19
```
