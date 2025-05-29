```
svp(atomicnumber::Int, temp::Real)
svp(element::String, temp::Real)
```

Saturated vapor pressure, *p* (in Pa), of a given `element` for a given  temperature *T* (in K),

$$
\mathrm{log_{e}}p=A+B/T+C\mathrm{log_{10}}T+D\cdot T/1000,
$$

where A,B,C,D, are the Antoine coefficients collected in  [`CamiXon.dictAntoineCoefficient`](@ref).

#### Examples:

```
julia> svp("Li", 623.0)
0.0015230367024569058
```
