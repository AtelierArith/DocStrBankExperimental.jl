```Julia
QCDoriginal = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ*α,𝟏/μₚₑ)
```

量子色力学（オリジナル） `UnitSystem` は `protonmass` と `elementarycharge` でスケーリングされています。

```Julia
julia> boltzmann(QCDoriginal)
1

julia> planckreduced(QCDoriginal)
1

julia> lightspeed(QCDoriginal)
1

julia> vacuumpermeability(QCDoriginal)
0.09170123688926637

julia> electronmass(QCDoriginal)
0.0005446170214868301
```

よく知られている `QCDoriginal` の長さ、時間、質量、電荷の値は次の通りです：

```Julia
julia> length(QCDoriginal,SI2019) # lQCD
2.1030891033504994e-16

julia> time(QCDoriginal,SI2019) # tQCD
7.015150138802022e-25

julia> mass(QCDoriginal,SI2019) # mQCD
1.6726219236940502e-27

julia> charge(QCDoriginal,SI2019) # qQCD
1.602176634e-19
```
