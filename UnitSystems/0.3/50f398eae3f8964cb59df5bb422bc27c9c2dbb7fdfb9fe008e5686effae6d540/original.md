```Julia
QCDGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,𝟏/μₚₑ)
```

Qunatum chromodynamics (Gauss) `UnitSystem` based on the `protonmass` scale.

```Julia
julia> boltzmann(QCDGauss)
1

julia> planckreduced(QCDGauss)
1

julia> lightspeed(QCDGauss)
1

julia> vacuumpermeability(QCDGauss)
12.566370614359172

julia> electronmass(QCDGauss)
0.0005446170214868301
```

The well known `QCDGauss` values for `length`, `time`, `mass`, and `charge` are:

```Julia
julia> length(QCDGauss,SI2019) # lQCD
2.1030891033504994e-16

julia> time(QCDGauss,SI2019) # tQCD
7.015150138802022e-25

julia> mass(QCDGauss,SI2019) # mQCD
1.6726219236940502e-27

julia> charge(QCDGauss,SI2019) # qQCD
1.8755460377789286e-18
```
