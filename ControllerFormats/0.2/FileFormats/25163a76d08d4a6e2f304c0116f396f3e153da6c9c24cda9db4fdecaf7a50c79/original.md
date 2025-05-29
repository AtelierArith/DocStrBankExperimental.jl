```
read_YAML(filename::String)
```

Read a neural network stored in [YAML](https://yaml.org/) format. This function requires to load the [`YAML.jl` library](https://github.com/JuliaData/YAML.jl).

### Input

  * `filename` – name of the `YAML` file

### Output

A [`FeedforwardNetwork`](@ref).
