```Julia
QCD = UnitSystem(𝟏,𝟏,𝟏,𝟏,𝟏/μₚₑ)
```

量子色力学 `UnitSystem` は `protonmass` スケールに基づいています。

```Julia
julia> boltzmann(QCD)
1

julia> planckreduced(QCD)
1

julia> lightspeed(QCD)
1

julia> vacuumpermeability(QCD)
1

julia> electronmass(QCD)
0.0005446170214868301
```

よく知られている `QCD` の値は、`length`、`time`、`mass`、および `charge` です。

```Julia
julia> length(QCD,SI2019) # lQCD
2.1030891033504994e-16

julia> time(QCD,SI2019) # tQCD
7.015150138802022e-25

julia> mass(QCD,SI2019) # mQCD
1.6726219236940502e-27

julia> charge(QCD,SI2019) # qQCD
5.290817689895691e-19
```
