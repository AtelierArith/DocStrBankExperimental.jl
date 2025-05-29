```Julia
Natural = UnitSystem(𝟏,𝟏,𝟏,𝟏,𝟏)
```

Natural `UnitSystem` with all primary constants having unit value.

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

The well known `Natural` values for `length`, `time`, `mass`, and `charge` are:

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
