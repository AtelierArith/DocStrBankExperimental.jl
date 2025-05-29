```
read_weather(
    file[,args...];
    date_format = DateFormat("yyyy-mm-ddTHH:MM:SS.s"),
    hour_format = DateFormat("HH:MM:SS"),
    duration=nothing
)
```

Read a meteo file. The meteo file is a CSV, and optionnaly with metadata in a header formatted as a commented YAML. The column names **and units** should match exactly the fields of [`Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/#PlantMeteo.Atmosphere), or  the user should provide their transformation as arguments (`args`) with the `DataFrames.jl` form, *i.e.*: 

  * `:var_name => (x -> x .+ 1) => :new_name`: the variable `:var_name` is transformed by the function    `x -> x .+ 1` and renamed to `:new_name`
  * `:var_name => :new_name`: the variable `:var_name` is renamed to `:new_name`
  * `:var_name`: the variable `:var_name` is kept as is

# Note

The variables found in the file will be used *as is* if not transformed, and not recomputed from the other variables. Please check that all variables have the same units as in the [`Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/#PlantMeteo.Atmosphere) structure.

# Arguments

  * `file::String`: path to a meteo file
  * `args...`: A list of arguments to transform the table. See above to see the possible forms.
  * `date_format = DateFormat("yyyy-mm-ddTHH:MM:SS.s")`: the format for the `DateTime` columns
  * `hour_format = DateFormat("HH:MM:SS")`: the format for the `Time` columns (*e.g.* `hour_start`)
  * `duration`: a function to parse the `duration` column if present in the file. Usually `Dates.Day` or `Dates.Minute`.

If the column is absent, the duration will be computed using the `hour_format` and the `hour_start` and `hour_end` columns along with the `date` column.

# Examples

```julia
using PlantMeteo, Dates

file = joinpath(dirname(dirname(pathof(PlantMeteo))),"test","data","meteo.csv")

meteo = read_weather(
    file,
    :temperature => :T,
    :relativeHumidity => (x -> x ./100) => :Rh,
    :wind => :Wind,
    :atmosphereCO2_ppm => :Cₐ,
    date_format = DateFormat("yyyy/mm/dd")
)
```
