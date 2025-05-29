```
set_settings!(args, options::Dict{Tuple{Vararg{String}},<:Any})
```

Helper function to set multiple options at `path` to `value` and then regenerate the multinetwork data from `args`, where the paths are the keys of the `options` input dictionary.
