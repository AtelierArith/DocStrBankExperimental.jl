```
show_daily(city::String, i_row::Int64 = 1)
```

Shows the daily weather conditions for a given city.

# Arguments

  * `city::String` : Valid city name, e.g. "Oslo", "Paris", "Amsterdam" etc.
  * `i_row::Int64` : In case of more than one match for a given location,                  select the desired timezone by providing the row index                  from the printed DataFrame. Default is set to 1.

# Example

```julia-repl
julia> show_daily("Veldhoven")
┌────────────┬────────┬────────┬────────────┬────────────┬───────────┬────────────────┬─────────────┬─────────────────────┐
│       Time │ Min. T │ Max. T │ App. min T │ App. max T │ Prec. sum │ Prec. duration │ Prec. prob. │           Condition │
│     [date] │   [°C] │   [°C] │       [°C] │       [°C] │      [mm] │        [hours] │         [%] │                  [] │
├────────────┼────────┼────────┼────────────┼────────────┼───────────┼────────────────┼─────────────┼─────────────────────┤
│ 2023-02-26 │   -1.4 │    4.9 │       -5.7 │       -0.7 │       0.0 │            0.0 │           0 │       Partly cloudy │
│ 2023-02-27 │   -1.6 │    6.2 │       -5.1 │        1.4 │       0.0 │            0.0 │           0 │            Overcast │
│ 2023-02-28 │   -1.1 │    4.3 │       -5.0 │       -1.3 │       0.0 │            0.0 │           0 │       Partly cloudy │
│ 2023-03-01 │   -2.0 │    5.3 │       -6.4 │       -0.2 │       0.0 │            0.0 │           0 │            Overcast │
│ 2023-03-02 │   -1.2 │    6.7 │       -5.1 │        2.0 │       0.0 │            0.0 │           0 │       Partly cloudy │
│ 2023-03-03 │   -1.1 │    3.3 │       -4.9 │       -0.3 │       0.0 │            0.0 │           0 │ Depositing rime fog │
│ 2023-03-04 │   -0.8 │    7.5 │       -3.6 │        4.7 │       0.0 │            0.0 │           0 │                 Fog │
└────────────┴────────┴────────┴────────────┴────────────┴───────────┴────────────────┴─────────────┴─────────────────────┘
Europe/Amsterdam CET
[Weather data by Open-Meteo.com]
```
