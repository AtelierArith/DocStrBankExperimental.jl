```
saturation_ancillary(fluid_name::AbstractString, output::AbstractString, quality::Integer, input::AbstractString, value::Real)
```

Extract a value from the saturation ancillary.

# Arguments

  * `fluid_name`: The name of the fluid to be used - HelmholtzEOS backend only
  * `output`: The desired output variable ("P" for instance for pressure)
  * `quality`: The quality, 0 or 1
  * `input`: The input variable ("T")
  * `value`: The input value

# Example

julia> saturation_ancillary("R410A","I",1,"T", 300) 0.004877519938463293

# Ref

double saturation*ancillary(const char* fluid*name, const char* output, int Q, const char* input, double value);
