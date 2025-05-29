```
SingleFluidIdeal(components;
    userlocations = String[],
    Rgas = nothing,
    verbose = false,
    coolprop_userlocations = true)
```

## Input parameters

  * JSON data (CoolProp and teqp format)

## Input models

  * `ancillaries`: a model that provides initial guesses for saturation calculations. if `nothing`, then they will be parsed from the input JSON.

## Description

Instantiates the ideal part of a single-component Empiric EoS model. `Rgas` can be used to set the value of the gas constant that is used during property calculations.

If `coolprop_userlocations` is true, then Clapeyron will try to look if the fluid is present in the CoolProp library.

The properties and ideal terms can be accessed via the `properties` and `ideal` fields respectively:

```julia-repl
julia> model = SingleFluidIdeal("water")
Ideal MultiParameter Equation of state for water:
 Lead terms: -8.3204464837497 + 6.6832105275932*τ + 3.00632*log(τ)
 Plank-Einstein terms: 5

julia> model.ideal
Ideal MultiParameter coefficients:
 Lead terms: -8.3204464837497 + 6.6832105275932*τ + 3.00632*log(τ)
 Plank-Einstein terms: 5
```
