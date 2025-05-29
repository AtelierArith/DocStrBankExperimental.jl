```
SingleFluid(components;
        userlocations = String[],
        ancillaries = nothing,
        ancillaries_userlocations = String[],
        estimate_pure = false,
        coolprop_userlocations = true,
        Rgas = nothing,
        verbose = false)
```

## Input parameters

  * JSON data (CoolProp and teqp format)

## Input models

  * `ancillaries`: a model that provides initial guesses for saturation calculations. if `nothing`, then they will be parsed from the input JSON.

## Description

Instantiates a single-component Empiric EoS model. `Rgas` can be used to set the value of the gas constant that is used during property calculations.

If `coolprop_userlocations` is true, then Clapeyron will try to look if the fluid is present in the CoolProp library.

The properties, ideal and residual terms can be accessed via the `properties`, `ideal` and `residual` fields respectively:

```julia-repl
julia> model = SingleFluid("water")
MultiParameter Equation of state for water:
 Polynomial power terms: 7
 Exponential terms: 44
 Gaussian bell-shaped terms: 3
 Non Analytic terms: 2

julia> model.ideal
Ideal MultiParameter coefficients:
 Lead terms: -8.3204464837497 + 6.6832105275932*τ + 3.00632*log(τ)
 Plank-Einstein terms: 5

julia> model.residual
Residual MultiParameter coefficients:
 Polynomial power terms: 7
 Exponential terms: 44
 Gaussian bell-shaped terms: 3
 Non Analytic terms: 2
```
