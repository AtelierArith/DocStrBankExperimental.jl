```
get_time_array(@nospecialize(ids::IDS), field::Symbol, time0::Float64, scheme::Symbol=:constant)
```

Get data from time dependent array

NOTE: logic for @ddtime array handling:

  * interpolation (i) `scheme` between array bounds
  * constant (c) extrapolation within bounds of time array
  * error (e) when time0 is before minimum(time)

For example:

```
time:   -oooo-
data:   -o-o--
ddtime: eiiicc
```
