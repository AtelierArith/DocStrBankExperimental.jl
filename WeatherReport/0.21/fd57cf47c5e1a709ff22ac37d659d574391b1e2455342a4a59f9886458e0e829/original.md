```
plot_box_snow(city::String = "",
              i_row::Int64 = 1;
              lat::Float64 = 0.0,
              long::Float64 = 0.0,
              year::String = "2022")
```

Shows the monthly boxplot distribution of snowfall amount for the preceding hour in centimeter [cm] for a given location (city or lat/long).

# Arguments

  * `city::String` : Valid city name, e.g. "Oslo", "Paris", "Amsterdam" etc.
  * `i_row::Int64` : In case of more than one match for a given location,                  select the desired timezone by providing the row index                  from the printed DataFrame. Default is set to 1.
  * `year::String` : Year for which data needs to be shown, e.g. "2020"

# Optional keywords

  * `lat::Float64` : Geographical WGS84 coordinate of the location (°S < 0, °N > 0)
  * `long::Float64` : Geographical WGS84 coordinate of the location (°W < 0, °E > 0)

# Example

```julia-repl
julia> plot_box_snow("Tromso", year = "2023")
                            Tromso: Snowfall monthly distribution for 2023                
             Timezone: Europe/Oslo                      [Weather data by Open-Meteo.com]  
            ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ 
            ┃┬───┐                            ╷                                         ┃ 
    January ┃│   ├────────────────────────────┤                                         ┃ 
            ┃┴───┘                            ╵                                         ┃ 
            ┃┬───┐                                                                 ╷    ┃ 
   February ┃│   ├─────────────────────────────────────────────────────────────────┤    ┃ 
            ┃┴───┘                                                                 ╵    ┃ 
            ┃┬─┐                              ╷                                         ┃ 
      March ┃│ ├──────────────────────────────┤                                         ┃ 
            ┃┴─┘                              ╵                                         ┃ 
            ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ 
             0                                   1                                     2  
                                                 [cm]                                     
```
