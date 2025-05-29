```
plrs = extract_plr(sim::PLR_Simulation)
plr = extract_plr(p::Union{PLR_Simulation_Point,PLR_Result})
```

Extract the PLR value (as a number between 0 and 1) from either a `PLR_Simulation` or a single `PLR_Simulation_Point` or `PLR_Result`.

In the first case, the function will return a vector with an element for each load point in the `PLR_Simulation` object.
