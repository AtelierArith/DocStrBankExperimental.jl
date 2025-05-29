```
show_current(city::String, i_row::Int64 = 1)
```

Shows the current weather conditions for a given city.

# Arguments

  * `city::String` : Valid city name, e.g. "Oslo", "Paris", "Amsterdam" etc.
  * `i_row::Int64` : In case of more than one match for a given location,                  select the desired timezone by providing the row index                  from the printed DataFrame. Default is set to 1.

# Example

```julia-repl
julia> show_current("Lisbon")
[ Info: More than one match found, showing report for location in row 1.
[ Info: You can select another location by its row index.
8×4 DataFrame
 Row │ CITY     TIMEZONE          LATITUDE  LONGITUDE 
     │ String?  String31          Float64   Float64   
─────┼────────────────────────────────────────────────
   1 │ Lisbon   Europe/Lisbon      38.7167   -9.13333
   2 │ Lisbon   America/New_York   39.8609  -83.6352
   3 │ Lisbon   America/New_York   41.604   -72.0117
   4 │ Lisbon   America/Chicago    41.9211  -91.3855
   5 │ Lisbon   America/New_York   44.0315  -70.1045
   6 │ Lisbon   America/Chicago    46.4416  -97.6812
   7 │ Lisbon   America/New_York   44.2134  -71.9109
   8 │ Lisbon   America/New_York   40.772   -80.7681
┌───────────────┬───────────┬────────────┬─────────────┬───────────┬─────────┬─────────┐
│      Timezone │ Elevation │ Wind speed │ Temperature │ Condition │      🌅 │      🌆 │
│         [WET] │       [m] │     [km/h] │        [°C] │        [] │ [hh:mm] │ [hh:mm] │
├───────────────┼───────────┼────────────┼─────────────┼───────────┼─────────┼─────────┤
│ Europe/Lisbon │      48.0 │        9.1 │        12.5 │ Clear sky │    7:18 │   18:21 │
└───────────────┴───────────┴────────────┴─────────────┴───────────┴─────────┴─────────┘
```
