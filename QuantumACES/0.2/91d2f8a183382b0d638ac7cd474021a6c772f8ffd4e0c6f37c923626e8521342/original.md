```
is_additive(g::Gate; strict::Bool = false)
```

Returns `true` if the noise associated with the gate `g` can only be estimated to additive precision, and `false` otherwise. If `strict` is `true`, this is `true` only for state preparation and measurement noise, as is proper, otherwise it is also `true` for mid-circuit measurement and reset noise, and measurement idle noise.
