```
write_weather(
    file, w; 
    vars=setdiff(propertynames(w), ATMOSPHERE_COMPUTED),
    duration=Dates.Minute
)
```

Write the weather data to a file. 

# Arguments

  * `file`: a `String` representing the path to the file to write
  * `w`: a `TimeStepTable{Atmosphere}`
  * `vars`: a vector of variables to write (as symbols). By default, all variables are written except the ones that

can be recomputed (see [`ATMOSPHERE_COMPUTED`](@ref)). If `nothing` is given, all variables are written.

  * `duration`: the unit for formating the duration of the time steps. By default, it is `Dates.Minute`.

# Examples

```julia
using PlantMeteo, Dates

file = joinpath(dirname(dirname(pathof(PlantMeteo))),"test","data","meteo.csv")
w = read_weather(
    file,
    :temperature => :T,
    :relativeHumidity => (x -> x ./100) => :Rh,
    :wind => :Wind,
    :atmosphereCO2_ppm => :Cₐ,
    date_format = DateFormat("yyyy/mm/dd")
)

write_weather("meteo.csv", w)
```
