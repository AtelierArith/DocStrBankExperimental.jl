```
Projection(fp::AbstractFlowpipe, vars::NTuple{D,Int}) where {D}
```

Return the lazy projection of a flowpipe.

### Input

### Output

### Notes

The projection is lazy, and consists of mapping each set `X` in the flowpipe to `MX`, where `M` is the projection matrix associated with the given variables `vars`.
