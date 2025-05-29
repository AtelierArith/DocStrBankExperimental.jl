```Julia
Hartree = UnitSystem(𝟏,𝟏,𝟏/α,𝟐*τ*α^2,𝟏)
```

Hartree原子の`UnitSystem`は`bohr`半径と`elementarycharge`スケールに基づいています。

```Julia
julia> boltzmann(Hartree)
1

julia> planckreduced(Hartree)
1

julia> lightspeed(Hartree)
137.035999084

julia> vacuumpermeability(Hartree)
0.0006691762566203905

julia> electronmass(Hartree)
1
```

よく知られている`Hartree`原子単位の値は`length`、`time`、`mass`、および`charge`について次の通りです：

```Julia
julia> length(Hartree,SI2019) # lA
5.291772109022829e-11

julia> time(Hartree,SI2019) # tA
2.418884326585658e-17

julia> mass(Hartree,SI2019) # mA
9.109383701558256e-31

julia> charge(Hartree,SI2019) # qA
1.6021766340000001e-19
```
