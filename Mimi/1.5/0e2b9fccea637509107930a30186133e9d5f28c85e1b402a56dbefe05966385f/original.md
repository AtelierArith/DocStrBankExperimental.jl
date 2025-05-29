```
update_param!(m::Model, name::Symbol, value; update_timesteps = nothing)
```

Update the `value` of an model parameter in model `m`, referenced by `name`. The update_timesteps keyword argument is deprecated, we keep it here  just to provide warnings.
