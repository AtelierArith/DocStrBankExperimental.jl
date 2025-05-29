```
reduce_single_phase_loadbuses!(data::Dict; exclude = [])
```

Reduces the dimensions of voltage variables for load buses in which the connected load(s) only have one active phase.

```
- data: `MATHEMATICAL` data model of the network
- exclude: buses to which this transformation is not applied
```
