```Julia
QCDGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,𝟏/μₚₑ)
```

プロトン質量スケールに基づく量子色力学（ガウス）`UnitSystem`。

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

よく知られた`QCDGauss`の長さ、時間、質量、電荷の値は次のとおりです。

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
