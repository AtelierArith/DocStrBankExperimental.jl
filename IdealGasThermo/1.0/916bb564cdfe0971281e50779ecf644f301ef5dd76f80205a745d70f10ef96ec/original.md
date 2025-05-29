```
set_TP!(gas::AbstractGas, T::Float64, P::Float64)
```

Calculates state of the gas given Temperature and pressure (T,P) in K and Pa respectively.

# Examples

```julia-repl
julia> gas = Gas(); # Create an ideal gas consisting of air at std. conditions
julia> set_TP!(gas, 298.15*2, 101325.0*2)
Ideal Gas at
  T =  596.300 K
  P =  202.650 kPa
 cp =   30.418 J/K/mol
  h =    8.706 kJ/mol
  s =    0.214 kJ/K/mol

with composition:
-----------------------------
 Species        Yᵢ  MW[g/mol]
-----------------------------
     Air     1.000     28.965
-----------------------------
     ΣYᵢ     1.000     28.965
```
