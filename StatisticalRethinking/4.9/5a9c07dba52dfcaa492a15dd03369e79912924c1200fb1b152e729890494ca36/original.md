# sr_path

Relative path using the StatisticalRethinking src/ directory.

### Example to get access to the data subdirectory

```julia
sr_path("..", "data")
```

Note that in the projects, e.g. SR2StanPluto.jl and SR2TuringPluto.jl, the DrWatson approach is a better choics, i.e: `sr_datadir(filename)`
