```
outputs = basic_run(; kwargs...)
```

Runs a basic AquaCrop simulation, the `outputs` variable has the final dataframes with the results of the simulation

`runtype` allowed for now is `NormalFileRun` or `TomlFileRun`

`NormalFileRun` will use the input from a files like in AquaCrop Fortran (see AquaCrop.jl/test/testcase)

`TomlFileRun` will use the input from TOML files (see AquaCrop.jl/test/testcase/TOML_FILES)

You can see the daily result in `outputs[:dayout]` the result of each harvest in `outputs[:harvestsout]` the result of the whole season in `outputs[:seasonout]` the information for the evaluation in `outputs[:evaldataout]` and the logger information in `outputs[:logger]`
