```
set_h!(gas::AbstractGas, hspec::Float64)
```

Calculates gas temperature for a specified enthalpy via a non-linear  Newton-Raphson method.

# Examples

```julia-repl
julia> gas = Gas();
julia> set_h!(gas, 0.0)
Ideal Gas at
  T =  302.463 K
  P =  101.325 kPa
 cp =   29.108 J/K/mol
  h =    0.000 kJ/mol
  s =    0.199 kJ/K/mol

with composition:
-----------------------------
 Species        Yᵢ  MW[g/mol]
-----------------------------
     Air     1.000     28.965
-----------------------------
     ΣYᵢ     1.000     28.965
```
