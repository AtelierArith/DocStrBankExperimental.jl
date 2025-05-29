```
params, signal = load_nxs(filename; field="signal")
```

Given the name of a Mantid-exported `MDHistoWorkspace` file, load the [`BinningParameters`](@ref) and the signal from that file.

To load another field instead of the signal, specify e.g. `field="errors_squared"`. Typical fields include `errors_squared`, `mask`, `num_events`, and `signal`.
