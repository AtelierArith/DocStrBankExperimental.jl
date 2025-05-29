```
compare_box_windspeed(city::String = "",
                      i_row::Int64 = 1;
                      lat::Float64 = 0.0,
                      long::Float64 = 0.0,
                      month::String = "Jan",
                      num_years::Int64 = 5)
```

Compares the boxplot distribution of wind speed at 10 meter above ground for a given location (city or lat/long) for a given month across a given number of years.

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
julia> compare_box_windspeed("Copenhagen", month = "Feb", num_years = 2)
[ Info: More than one match found, showing report for location in row 1.
[ Info: You can select another location by its row index.
2×4 DataFrame
 Row │ CITY        TIMEZONE           LATITUDE  LONGITUDE 
     │ String?     String31           Float64   Float64   
─────┼────────────────────────────────────────────────────
   1 │ Copenhagen  Europe/Copenhagen   55.6759    12.5655
   2 │ Copenhagen  America/New_York    43.8934   -75.6735
                 Copenhagen: Wind speed comparison for Feb over last 2 years          
         Timezone: Europe/Copenhagen                [Weather data by Open-Meteo.com]  
        ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ 
        ┃╷             ┌────┬──────┐                 ╷                              ┃ 
   2021 ┃├─────────────┤    │      ├─────────────────┤                              ┃ 
        ┃╵             └────┴──────┘                 ╵                              ┃ 
        ┃╷                    ┌──────┬─────┐                      ╷                 ┃ 
   2022 ┃├────────────────────┤      │     ├──────────────────────┤                 ┃ 
        ┃╵                    └──────┴─────┘                      ╵                 ┃ 
        ┃ ╷           ┌───────┬────────┐                                          ╷ ┃ 
   2023 ┃ ├───────────┤       │        ├──────────────────────────────────────────┤ ┃ 
        ┃ ╵           └───────┴────────┘                                          ╵ ┃ 
        ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ 
         0                                   30                                   60  
                                            [km/h]                                    
```
