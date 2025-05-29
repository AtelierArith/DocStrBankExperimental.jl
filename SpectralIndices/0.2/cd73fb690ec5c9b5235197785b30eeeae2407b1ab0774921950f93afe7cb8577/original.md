```
Constant(constant::Dict{String, Any}) -> Constant
```

Create a `Constant` object from a dictionary.

# Arguments

  * `constant::Dict{String, Any}`: A dictionary containing the following keys:

      * `"description"`: Description of the constant.
      * `"short_name"`: Short name of the constant.
      * `"default"`: Default value of the constant.

# Returns

  * `Constant`: An instance of the `Constant` struct with fields populated based on the provided dictionary.

# Example

```julia
constant_dict = Dict(
    "description" => "Speed of light in vacuum", "short_name" => "c", "default" => 299792458
)
constant = Constant(constant_dict)
```
