```
add_nominal_load!(config, data)
```

Add load power in `config[:load_add_file]` to load elements after the annual match in [`match_nominal_load!`](@ref)

We may wish to provide additional load after the match so that we can compare the difference.
