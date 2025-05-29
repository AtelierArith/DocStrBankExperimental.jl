```
layer_included(m::Meta, only_layers, ignore_layers)
```

Return whether `m` or `layer(m)` is included based on inclusion/exclusion rules.

Both `only_layers` and `ignore_layers` are collections of `DeviceLayout.Meta` and/or layer name `Symbol`s.

If `only_layers` is empty, then only `ignore_layers` is used, and `layer_included` checks that neither `m` nor `layer(m)` is in `ignore_layers`. Otherwise, `layer_included` also checks that `m` or `layer(m)` is in `only_layers`.
