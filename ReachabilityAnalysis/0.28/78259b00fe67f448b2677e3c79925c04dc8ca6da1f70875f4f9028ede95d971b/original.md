```
HybridFlowpipe{N,RT<:AbstractReachSet{N},FT<:AbstractFlowpipe} <: AbstractFlowpipe
```

Type that wraps a vector of flowpipes of the same type, such that they are contiguous in time.

### Fields

  * `Fk`  – vector of flowpipes
  * `ext` – (optional, default: empty) dictionary for extensions

### Notes

The evaluation functions (in time) for this type do not assume that the flowpipes are contiguous in time. That is, the final time of the `i`-th flowpipe does not match the start time of the `i+1`-th flowpipe.
