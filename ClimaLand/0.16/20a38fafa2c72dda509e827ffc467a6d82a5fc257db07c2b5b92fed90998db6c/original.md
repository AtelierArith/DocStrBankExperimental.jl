```
add_drivers_to_cache(p::NamedTuple, model::AbstractModel, coords)
```

Creates the driver variable NamedTuple (atmospheric and radiative forcing, etc), and merges it into `p` under the key `drivers`. If no driver variables are required, `p` is returned unchanged.
