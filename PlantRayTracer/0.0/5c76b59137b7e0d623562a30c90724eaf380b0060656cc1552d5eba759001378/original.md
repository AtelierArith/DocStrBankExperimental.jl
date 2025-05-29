```
TwoSidedSensor(nw::Int)
```

Create a sensor material object to store power for `nw` wavelengths. A two-sided sensor material will let rays pass through without altering the direction or irradiance. They will also not count for the total number of ray iterations. The accumulated power is stored separately for rays hitting on the front and back side of the sensor.

## Examples

```jldoctest
julia> s = TwoSidedSensor(1);

julia> s = TwoSidedSensor(3);
```
