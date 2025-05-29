```
ParamDict(data::Dict, override_dict::Union{Nothing,Dict})
```

Structure to hold information read-in from TOML file, as well as a parametrization type `FT`.

Uses the name to search

# Fields

  * `data`: dictionary representing a default/merged parameter TOML file
  * `override_dict`: either a nothing, or a dictionary representing an override parameter TOML file
