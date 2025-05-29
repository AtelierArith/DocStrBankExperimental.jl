```
abstract type Modification
```

Modification represents an abstract type for really anything that would make changes to a model.

`Modification`s represent ways to modify the behavior of E4ST.  Some possible examples of `Modifications` (not necessarily implemented) include:

  * Scale the NG price for each year
  * Enforce a cap on carbon emissions in Colorado.
  * Adding a national CES with changing target and benchmark rate
  * Preventing the addition of new Nuclear Generation in PJM
  * Logging a custom calculated result to file
  * Plotting and saving a heat map of emissions by state as part of the results processing
  * The sky is the limit!

## Defining a `Modification`

When defining a concrete `Modification` type, you should know the following.

  * Since Modifications are specified in a YAML config file, `Modification`s must be constructed with keyword arguments.  `Base.@kwdef` may come in handy here.
  * All `Modication`s are paired with a name in the config file.  That name is automatically passed in as a keyword argument to the `Modification` constructor if the type has a `name` field.  The `name` will be passed in as a `Symbol`.

`Modification`'s can modify things in up to four places, with the default behavior of the methods being to make no changes:

  * [`modify_raw_data!(mod, config, data)`](@ref) - In the data preparation step, right after [`read_data_files!(config, data)`](@ref) before setting up the data
  * [`modify_setup_data!(mod, config, data)`](@ref) - In the data preparation step, right after [`setup_data!(config, data)`](@ref) before setting up the `Model`
  * [`modify_model!(mod, config, data, model)`](@ref) - In the model setup step, after setting up the DC-OPF but before optimizing
  * [`modify_results!(mod, config, data)`](@ref) - After optimizing the model, in the results generation step

Modifications get printed to YAML when the config file is saved at the beginning of a call to `run_e4st`.  If you implement a Modification for which it is undesirable to print every field, you can implement the following interface:

  * [`fieldnames_for_yaml(::Type)`](@ref) - returns the desired fieldnames as a collection of `Symbol`s

Modification can be given a rank which will determine the order that they are called in when modifying the model. This can be important if a mod requires information calculated in a previous mod or needs to be applied on top of another mod.  Ranks is specified by defining a method for [`mod_rank(::Type{<:Modification})`](@ref). The default rank is 0. Modifications that setup data and model features like `CCUS` and `DCLines` can have negative values to signify that they are called before while mods like policies would have a positive rank meaning they would modify the model after the setup mods. 

## Specifying a `Modification` in the config file YAML

`Modifications` must be be specified in the config file.  They must have a type key, and keys for each other desired keyword argument in the constructor.

## An Example

Say we want to make a Modification to change the price of natural gas based on a table in a CSV file.

```julia
using E4ST, CSV, DataFrames
struct UpdateNGPrice <: Modification
    filename::String
    prices::DataFrame
end

# Define kwarg constructor
function UpdateNGPrice(; filename=nothing)
    filename === nothing && error("Must provide UpdateNGPrice with a filename")
    prices = CSV.read(filename, DataFrame)
    return UpdateNGPrice(filename, prices)
end

# Make sure YAML doesn't try printing out the whole prices table
function E4ST.fieldnames_for_yaml(::Type{UpdateNGPrice})
    return (:filename,)
end

function E4ST.modify_raw_data!(mod::UpdateNGPrice, config, data)
    # update the price of natural gas from mod.prices here
end
```

Now, to add this to the `mods` list in the config file:

```yaml
mods:
  ...                                   # other mods as needed
  update_ng_price:                      # This is the name of the mod
    type: UpdateNGPrice
    filename: "C:/path/to/file.csv"
  ...                                   # other mods as needed
```
