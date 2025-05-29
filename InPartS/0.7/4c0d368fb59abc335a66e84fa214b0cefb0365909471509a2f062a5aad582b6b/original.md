```
AbstractRegistrar(dict::Dict{String, Any}) → concrete subtype of AbstractRegistrar
```

Creates a new registrar from a dictionary. This function can be used for all subtypes of `AbstractRegistrar` that provide a constructor accepting all fields as keyword arguments.

The type of the registrar is parsed from the value of `dict["_type"]`.
