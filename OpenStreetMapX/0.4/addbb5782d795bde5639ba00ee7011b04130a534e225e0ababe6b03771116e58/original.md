```
get_google_route(origin::Int, destination::Int, waypoint::Int,
                 map_data:MapData, googleapi_key::String;
                 googleapi_parameters::Dict{Symbol,String} = googleAPI_parameters)
```

Get route from to based on Google Distances API with three points (`origin`, `destination` and `waypoint` between) on map `map_data` using Google API key `googleapi_key` with optional Google Distances API request parameters `googleapi_parameters`.
