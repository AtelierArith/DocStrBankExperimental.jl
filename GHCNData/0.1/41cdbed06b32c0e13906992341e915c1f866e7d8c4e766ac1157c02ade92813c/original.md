```
select_data(
    time_interval::Tuple{Date, Date},
    lat_interval::Tuple{Real, Real},
    lon_interval::Tuple{Real, Real},
    element::String,
)
```

Load all of the data from a particular region and time period of type `element` e.g. `TMAX`. See section III of NOAA's readme [1] for more details on available elements.

Returns the results in a ...

Example:

```julia
using Dates, GHCNData
lat_interval = (50, 60);
lon_interval = (-10, 2);
time_interval = (Date(2010), Date(2020));
element = "TMAX"
data = select_data(time_interval, lat_interval, lon_interval, element)
```

[1] - https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt
