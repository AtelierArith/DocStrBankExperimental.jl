```
FuelPrice(;file, fp_scalar=1e3) <: Modification
```

FuelPrice is a [`Modification`](@ref) allowing users to specify fuel prices for different fuels by region.  If multiple steps and quantities are given, the fuel price for a given region will be computed endogenously.

  * [`modify_raw_data!(mod::FuelPrice, config, data)`](@ref)
  * [`modify_setup_data!(mod::FuelPrice, config, data)`](@ref)
  * [`modify_model!(mod::FuelPrice, config, data, model)`](@ref)
  * [`modify_results!(mod::FuelPrice, config, data)`](@ref)

To adjust price by hour or year, see [`AdjustHourly`](@ref) or [`AdjustYearly`](@ref).

## Fields

  * `file` - file path to the table of fuel steps. See [`summarize_table(::Val{:fuel_price})`]@(ref)
  * `fp_scalar = 1e3` - a `Float64` for how much to scale the fuel price variables by.  This helps with numerical instability, given that some fuel steps can be very large and could bloat the RHS and bounds range of the model.  The default value of 1e3, for example, means that the quantity variables will all be in terms of thousands of MMBtu rather than MMBtu.
