```Julia
planck(U::UnitSystem) = turn(x)*planckreduced(x)
```

プランク定数 `𝘩` は電磁周波数あたりのエネルギー（J⋅s または ft⋅lb⋅s）です。

```Julia
julia> planck(SI2019) # J⋅s
6.62607015e-34

julia> planck(SI2019)*lightspeed(SI2019) # J⋅m
1.9864458571489286e-25

julia> planck(CODATA) # J⋅s
6.626070039088792e-34

julia> planck(Conventional) # J⋅s
6.626068854361326e-34

julia> planck(SI2019)/elementarycharge(SI2019) # eV⋅s
4.135667696923859e-15

julia> planck(SI2019)*lightspeed(SI2019)/elementarycharge(SI2019) # eV⋅m
1.2398419843320026e-6

julia> planck(British) # ft⋅lb⋅s
4.887138541095932e-34
```
