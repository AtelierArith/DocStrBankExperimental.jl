```
latent_heat_vaporization(atomicnumber::Int, temp::Real)
latent_heat_vaporization(element::String, temp:Real)
```

Latent heat of vaporization, *L*(*T*) (in Joule/K), of a given `element`  for temperature *T* (in K), 

$$
L(T) = -(B +C\cdot T \mathrm{log_{10}}T+D\cdot T^2/1000),
$$

where A,B,C,D, are the Antoine coefficients collected in  [`CamiXon.dictAntoineCoefficient`](@ref).

#### Example:

```
julia> latent_heat_vaporization("Li", 623.0)
-18473.64020109123
```
