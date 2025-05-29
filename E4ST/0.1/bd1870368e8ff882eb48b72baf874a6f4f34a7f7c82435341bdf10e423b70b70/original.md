```
Retrofit <: Modification
```

Abstract supertype for retrofits.  Must implement the following interfaces:

  * (required) [`can_retrofit(ret::Retrofit, gen::DataFrameRow)`](@ref)`-> ::Bool` - returns whether or not a generator row can be retrofitted.
  * (required) [`retrofit!(ret::Retrofit, gen)`](@ref)`-> newgen::AbstractDict` - returns a new row to be added to the gen table.
  * (optional) [`init!(ret::Retrofit, config, data)`](@ref) - initialize data with the `Retrofit` by adding any necessary columns to the gen table, etc.  Defaults to do nothing.

The following methods are defined for `Retrofit`, so you do not define any of the ordinary `Modification` methods for any subtype of `Retrofit` - only implement the above interfaces.

  * [`modify_setup_data!(ret::Retrofit, config, data)`](@ref)
  * [`modify_model!(ret::Retrofit, config, data, model)`](@ref)
