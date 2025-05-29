```
get_prior(param_dict::AbstractDict; names = nothing)
get_prior(prior_path::AbstractString; names = nothing)
```

Constructs the combined prior distribution from a `param_dict` or a TOML configuration file specified by `prior_path`. If `names` is provided, only those parameters are used.
