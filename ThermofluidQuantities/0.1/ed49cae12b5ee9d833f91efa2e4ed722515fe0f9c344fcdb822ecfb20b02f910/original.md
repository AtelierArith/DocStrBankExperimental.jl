```
@dimvar name utype
```

Define a dimensional variable type of the given name, with units of type `utype`. The `utype` is of the form created with the @displayedunits macro. A list of such types can be found in `ThermofluidQuantities.unittypes`.

# Examples

```jldoctest mydimvar
julia> import ThermofluidQuantities: 𝐓

julia> @displayedunits MyTimeType "s" 𝐓

julia> @dimvar MyTimeVar MyTimeType

julia> MyTimeVar(5)
MyTimeVar = 5.0 s
```
