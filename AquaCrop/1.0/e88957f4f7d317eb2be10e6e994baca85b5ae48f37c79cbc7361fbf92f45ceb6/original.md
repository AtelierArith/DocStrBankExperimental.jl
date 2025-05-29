```
change_climate_data!(cropfield::AquaCropField, climate_data::DataFrame; kwargs...)
```

Changes the climate data in the `cropfield` using the data in `climate_data`.

Note that `climate_data` must have a column with `:Date` property, other wise we do not change anything. The function assumes that `:Date` goes day by day.

`climate_data` must also have one of the following climate properties `[:Tmin, :Tmax, :ETo, :Rain]`.
