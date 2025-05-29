```
organise_obs(f, data; obsdim=_default_obsdim(data))
organise_obs(::ObsArrangement, data; obsdim=_default_obsdim(data))
```

Organise the `data` according to the `ObsArrangement` expected by `f`.

# Arguments

  * `f`: the function or method needing the data in a certain orientation
  * `data`: the data to transform
  * `obsdim`: the dimension of the observations, resorts to `_default_obsdim` when not specified.
