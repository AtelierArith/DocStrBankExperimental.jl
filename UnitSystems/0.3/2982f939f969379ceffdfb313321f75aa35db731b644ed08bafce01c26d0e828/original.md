```Julia
boltzmann(U::UnitSystem) = molargas(x)/avogadro(x)
```

Boltzmann constant `kB` is the entropy amount of a unit number microstate permutation.

```Julia
julia> boltzmann(SI2019) # J⋅K⁻¹
1.380649e-23

julia> boltzmann(Metric) # J⋅K⁻¹
1.3806489995254104e-23

julia> boltzmann(SI2019)/elementarycharge(SI2019) # eV⋅K⁻¹
8.617333262145179e-5

julia> boltzmann(SI2019)/planck(SI2019) # Hz⋅K⁻¹
2.0836619123327576e10

julia> boltzmann(CGS) # erg⋅K⁻¹
1.3806489995254102e-16

julia> boltzmann(SI2019)/calorie(SI2019) # calᵢₜ⋅K⁻¹
3.297672849800614e-24

julia> boltzmann(SI2019)*°R/calorie(SI2019) # calᵢₜ⋅°R⁻¹
1.832040472111452e-24

julia> boltzmann(Brtish) # ft⋅lb⋅°R⁻¹
5.657302463819266e-24

julia> boltzmann(SI2019)/planck(SI2019)/lightspeed(SI2019) # m⁻¹⋅K⁻¹
69.50348004861274

julia> avogadro(SI2019)*boltzmann(SI2019)/calorie(SI2019) # calᵢₜ⋅mol⁻¹⋅K⁻¹
1.9859050081929635

julia> dB(boltzmann(SI2019)) # dB(W⋅K⁻¹⋅Hz⁻¹)
-228.59916717321767
```
