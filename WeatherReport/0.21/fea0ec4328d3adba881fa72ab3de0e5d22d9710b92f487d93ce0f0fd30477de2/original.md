```
compare_box_snow(city::String = "",
                 i_row::Int64 = 1;
                 lat::Float64 = 0.0,
                 long::Float64 = 0.0,
                 month::String = "Jan",
                 num_years::Int64 = 5)
```

Compares the boxplot distribution of snowfall amount for the preceding hour in centimeter [cm] for a given location (city or lat/long) for a given month across a given number of years.

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
julia> compare_box_snow("Turku", month = "Jan", num_years = 3)
                     Turku: Snowfall comparison for Jan over last 3 years             
         Timezone: Europe/Helsinki                  [Weather data by Open-Meteo.com]  
        ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ 
        ┃┐                                   ╷                                      ┃ 
   2020 ┃├───────────────────────────────────┤                                      ┃ 
        ┃┘                                   ╵                                      ┃ 
        ┃┬─┐                                 ╷                                      ┃ 
   2021 ┃│ ├─────────────────────────────────┤                                      ┃ 
        ┃┴─┘                                 ╵                                      ┃ 
        ┃┐                                                          ╷               ┃ 
   2022 ┃├──────────────────────────────────────────────────────────┤               ┃ 
        ┃┘                                                          ╵               ┃ 
        ┃┐                                   ╷                                      ┃ 
   2023 ┃├───────────────────────────────────┤                                      ┃ 
        ┃┘                                   ╵                                      ┃ 
        ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ 
         0                                   1                                     2  
                                             [cm]                                     
```
