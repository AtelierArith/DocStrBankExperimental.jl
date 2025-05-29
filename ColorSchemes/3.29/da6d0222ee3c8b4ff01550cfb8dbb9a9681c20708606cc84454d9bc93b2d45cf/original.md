```
colorschemes
```

An exported dictionary of pre-defined colorschemes:

```julia
colorschemes[:summer] |> show
   ColorScheme(
      ColorTypes.RGB{Float64}[
          RGB{Float64}(0.0,0.5,0.4), RGB{Float64}(0.01,0.505,0.4), RGB{Float64}(0.02,0.51,0.4), RGB{Float64}(0.03,0.515,0.4),
          ...
```

To choose a random ColorScheme:

```julia
scheme = rand(keys(colorschemes))
```
