```Julia
loschmidt(U::UnitSystem) = atmosphere(U)/boltzmann(U)/temperature(T₀,SI2019,U)
```

Number of molecules (number density) of an ideal gas in a unit volume (m⁻³ or ft⁻³).

```Julia
julia> loschmidt(SI2019) # m⁻³
2.686780111798444e25

julia> loschmidt(Metric,atm,T₀) # m⁻³
2.6867801127220084e25

julia> loschmidt(Conventional,atm,T₀) # m⁻³
2.6867806380857353e25

julia> loschmidt(CODATA,atm,T₀) # m⁻³
2.686781068368475e25

julia> loschmidt(SI1976,atm,T₀) # m⁻³
2.6868261999086737e25

julia> loschmidt(English) # ft⁻³
7.608114025223316e23

julia> loschmidt(IAU) # au⁻³
8.995148987922053e58
```
