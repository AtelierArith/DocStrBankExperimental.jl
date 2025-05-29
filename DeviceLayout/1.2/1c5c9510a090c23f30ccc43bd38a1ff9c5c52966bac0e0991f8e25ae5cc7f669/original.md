```
layer_inclusion(only_layers, ignore_layers)
```

Return a function `f(m::Meta)` that returns a `Bool` based on inclusion/exclusion rules.

Both `only_layers` and `ignore_layers` are  `DeviceLayout.Meta`, layer name `Symbol`s, and/or collections of either.

If `only_layers` is empty, then only `ignore_layers` is used, and `f(m)` checks that neither `m` nor `layer(m)` is in `ignore_layers`. Otherwise, `f(m)` also checks that `m` or `layer(m)` is in `only_layers`.
