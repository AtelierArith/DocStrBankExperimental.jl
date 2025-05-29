```
set_defaults!(nw::Network, s::NWState)
```

Set the default values of the network to the values of the given state. Can be used to "store" the found fixpoint in the network metadata.

Values of `missing`, `nothing` or `NaN` are ignored.
