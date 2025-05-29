```
update_links!(model)
update_links!(params)
```

Recompute the current values of all parameters.

Typically when a new value of a parameter is assigned, all parameter links and aliases that depend on it are updated recursively. If a parameter is mutable, e.g. a Vector or another collection, its value can be updated in place without re-assigning the parameter, thus the automatic update does not happen. In this case, it is necessary to call `update_links!` manually.
