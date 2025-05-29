# `rel_path_cmdstan`

Relative path using the CmdStan.jl src directory. This approach has been copied from [DynamicHMCExamples.jl](https://github.com/tpapp/DynamicHMCExamples.jl)

### Example to get access to the data subdirectory

```julia
rel_path_cmdstan("..", "data")
```
