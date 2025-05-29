```
ShiftedFlowpipe{FT<:AbstractFlowpipe, NT<:Number} <: AbstractFlowpipe
```

Type that lazily represents a flowpipe that has been shifted in time.

### Fields

  * `F`  – original flowpipe
  * `t0` – time shift

### Notes

This type can wrap any concrete subtype of `AbstractFlowpipe`, and the extra field `t0` is such that the time spans of each reach-set in `F` are shifted by the amount `t0` (which should be a subtype of `Number`).
