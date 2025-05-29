```
Sensor(nw::Int)
```

Create a sensor material object to store power for `nw` wavelengths. A sensor material will let rays pass through without altering the direction or irradiance. They will also not count for the total number of ray iterations.

## Examples

```jldoctest
julia> s = Sensor(1);

julia> s = Sensor(3);
```
