```
(F::Fluid)(P,T)
```

General function for every subtype of fluid. This function calls every property calculation for the appropriate type at the point of `P` [Pa] and `T` [K].

# Arguments

  * `P`: Pressure [Pa].
  * `T`: Temperature [K].

# Output

  * `output::NamedTuple`: Named tuple with all the properties calculated.

```julia
(
    ρ=density [kg/m³],
    κ=compressibility [1/Pa],
    β=expansivity [1/K],
    C=specific heat [J/kg K],
    k=thermal conductivity [W/m K],
    μ=dynamic viscosity [Pa s]
)
```
