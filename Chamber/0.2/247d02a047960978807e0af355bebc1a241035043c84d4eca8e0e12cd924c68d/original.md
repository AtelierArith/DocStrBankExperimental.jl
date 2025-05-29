```
solve_NR(f, f_prime, errorTol::T, count_max::T, Xc_initial::T)::T where {T<:Float64}
```

  * Finding mole fraction of CO2 in gas (X_CO2).
  * This function is used within the `exsolve3` function.

## Arguments

  * `f`: Water Paritioning Function
  * `f_prime`: Function for the derivative of water with reference to X_CO2
  * `errorTol`: error tolerance, the default value is 1e-10
  * `count_max`: Maximum loop count, the default value is 1e2
  * `Xc_initial`: initial guess of X_CO2, the dedault value is 1e-2

## Returns

  * `X_CO2`: mole fraction of CO2 in gas
