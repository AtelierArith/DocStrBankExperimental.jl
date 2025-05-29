```
enable_species!(system; kwargs...)
```

Keyword arguments:

  * `species`: Integer or vector of integers. Species to be added to the system.
  * `regions`: Vector of integers. Regions, where these species shall be added.If `nothing`, they are added to all species.

Once a species has been added, it cannot be removed.
