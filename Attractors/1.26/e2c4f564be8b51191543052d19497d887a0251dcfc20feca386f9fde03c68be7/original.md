```
basins_of_attraction(mapper::AttractorsViaRecurrences; show_progress = true)
```

This is a special method of `basins_of_attraction` that using recurrences does *exactly* what is described in the paper by Datseris & Wagemakers [Datseris2022](@cite). By enforcing that the internal grid of `mapper` is the same as the grid of initial conditions to map to attractors, the method can further utilize found exit and attraction basins, making the computation faster as the grid is processed more and more.
