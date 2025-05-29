```
TimeSteppingStrategy(dict::Dict{String, Any}) → tss::TimeSteppingStrategy
```

Creates a new [`TimeSteppingStrategy`](@ref) from a dictionary. This function can be used for all subtypes of `TimeSteppingStrategy` that provide a constructor accepting all fields as keyword arguments.

The type of the `TimeSteppingStrategy` is parsed from the value of `dict["tssType"]`.  Note that type parameters specified in this string are discarded. They should therefore be inferrable from the other field values.

The type parsing uses [`reconstruct_subtype`](@ref) to find all the concrete leaves of the tree below the type `TimeSteppingStrategy`.
