```
listecmwfvars(source::Symbol=:reanalysis; single::Bool=true, levlist::Bool=false, contain::AbstractString="")
```

Print a list of CDS ERA5 variables.

### Args

  * `source`: The source of the data. It can be either $:reanalysis$ or $:forecast$. Default is `:reanalysis`.

### Kwargs

  * `single`: If true, only single-level variables are listed. If false, pressure-level variables are listed [Default is true].
  * `pressure`: If true, only pressure-level variables are listed. If false, single-level variables are listed.
  * `contain`: A string to filter the variables by their Name. Only those containing this string (case sensitive) are listed. If not provided, all variables are listed.

#### Example

```julia
# Print all pressure-level variables.
listecmwfvars(pressure=true)

# Print only single-level variables containing "Temperature" in their name from the foorecast datasets.
listecmwfvars(:forecast, contain="Temperature")
```
