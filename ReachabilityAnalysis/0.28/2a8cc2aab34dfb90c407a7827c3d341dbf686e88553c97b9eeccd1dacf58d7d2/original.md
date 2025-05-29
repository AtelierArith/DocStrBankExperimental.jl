```
MixedFlowpipe{N,RT<:AbstractReachSet{N},FT<:AbstractFlowpipe} <: AbstractFlowpipe
```

Type that wraps a vector of flowpipes of the same time, such that they are not necessarily contiguous in time.

### Fields

  * `Fk`  – vector of flowpipes
  * `ext` – (optional, default: empty) dictionary for extensions

### Notes

This type does not assume that the flowpipes are contiguous in time.
