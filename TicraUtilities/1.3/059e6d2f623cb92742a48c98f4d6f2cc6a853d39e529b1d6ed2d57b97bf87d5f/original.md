```
TorObj
```

Struct containing a single, general, TOR object.

## Fields

  * `name::String`: The name of the TOR object. Example: "my_rim".
  * `objtype::String`: The type of the TOR object. Example: "tabulated*rim*xy".
  * `propname::Vector{String}`: Names of object properties. Example:  ["file*name", "unit", "number*of*points", "translation", "polar*origin"]
  * `propval::Vector{String}`: Values of object properties corresponding to the names in `propnames`. Example: ["h*9m*scalloped_rim.xyz", "in", "112", "struct(x: 0.0 in, y: 0.0 in)",  "struct(status: automatic, x: 0.0 in, y: 0.0 in)"]

Note that the "values" in `propval` are simply strings that must be parsed for any numeric values that might be present.

## See Also

  * `parse_tor_struct`
