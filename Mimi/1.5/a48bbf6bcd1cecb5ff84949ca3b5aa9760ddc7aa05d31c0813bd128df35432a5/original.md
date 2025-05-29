```
update_param!(obj::AbstractCompositeComponentDef, name::Symbol, value; update_timesteps = nothing)
```

Update the `value` of a model parameter in composite `obj`, referenced by `name`. The update_timesteps keyword argument is deprecated, we keep it here  just to provide warnings.
