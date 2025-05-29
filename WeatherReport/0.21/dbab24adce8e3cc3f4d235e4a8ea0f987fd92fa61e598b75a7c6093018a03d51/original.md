```
compare_box_solar(city::String = "",
                  i_row::Int64 = 1;
                  lat::Float64 = 0.0,
                  long::Float64 = 0.0,
                  month::String = "Jan",
                  num_years::Int64 = 5)
```

Compares the boxplot distribution of shortwave solar radiation as average of the preceding hour for a given location (city or lat/long) for a given month across a given number of years. This is equal to the total global horizontal irradiation.

# Arguments

  * `city::String` : Valid city name, e.g. "Oslo", "Paris", "Amsterdam" etc.
  * `i_row::Int64` : In case of more than one match for a given location,                  select the desired timezone by providing the row index                  from the printed DataFrame. Default is set to 1.

# Mandatory keywords

  * `month::String` : Month for which data needs to be compared, e.g. "Jan", "March" etc.
  * `num_years::Int64` : Number of years across which the data will be compared

# Optional keywords

  * `lat::Float64` : Geographical WGS84 coordinate of the location (°S < 0, °N > 0)
  * `long::Float64` : Geographical WGS84 coordinate of the location (°W < 0, °E > 0)

# Example

```julia-repl
julia> compare_box_solar("Chennai", month = "Sept", num_years = 2)
              Chennai: Shortwave radiation comparison for Sept over last 2 years      
         Timezone: Asia/Kolkata                     [Weather data by Open-Meteo.com]  
        ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ 
        ┃┬──────────────────────────┐                                          ╷    ┃ 
   2021 ┃│                          ├──────────────────────────────────────────┤    ┃ 
        ┃┴──────────────────────────┘                                          ╵    ┃ 
        ┃┬─────────────────────────────┐                                         ╷  ┃ 
   2022 ┃│                             ├─────────────────────────────────────────┤  ┃ 
        ┃┴─────────────────────────────┘                                         ╵  ┃ 
        ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ 
         0                                  500                                1 000  
                                           [W/m^2]                                   
```
