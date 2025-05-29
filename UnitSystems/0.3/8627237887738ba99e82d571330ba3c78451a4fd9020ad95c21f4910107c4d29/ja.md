```Julia
planckreduced(U::UnitSystem) = planck(x)/turn(x)
```

縮小されたプランク定数 `ħ` は、プランク毎ラジアン (J⋅s⋅rad⁻¹ または ft⋅lb⋅s⋅rad⁻¹) です。

```Julia
julia> planckreduced(SI2019) # J⋅s⋅rad⁻¹
1.0545718176461565e-34

julia> planckreduced(SI2019)*lightspeed(SI2019) # J⋅m⋅rad⁻¹
3.1615267734966903e-26

julia> planckreduced(CODATA) # J⋅s⋅rad⁻¹
1.0545717999940896e-34

julia> planckreduced(Conventional) # J⋅s⋅rad⁻¹
1.054571611438857e-34

julia> planckreduced(SI2019)/elementarycharge(SI2019) # eV⋅s⋅rad⁻¹
6.582119569509067e-16

julia> planckreduced(SI2019)*lightspeed(SI2019)/elementarycharge(SI2019) # eV⋅m⋅rad⁻¹
1.973269804593025e-7

julia> planckreduced(British) # ft⋅lb⋅s⋅rad⁻¹
7.778122563903315e-35
```
