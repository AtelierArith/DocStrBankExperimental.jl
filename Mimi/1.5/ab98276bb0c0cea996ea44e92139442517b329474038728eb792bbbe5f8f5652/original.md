```
update_params!(m::Model, parameters::Dict; update_timesteps = nothing)
```

For each (k, v) in the provided `parameters` dictionary, `update_param!` is called to update the model parameter identified by k to value v.

For updating unshared parameters, each key k must be a Tuple matching the name of a  component in `obj` and the name of an parameter in that component.

For updating shared parameters, each key k must be a symbol or convert to a symbol  matching the name of a shared model parameter that already exists in the model.
