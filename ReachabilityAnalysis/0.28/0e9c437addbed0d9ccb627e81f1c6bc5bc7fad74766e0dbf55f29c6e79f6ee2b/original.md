```
LazySets.ρ(d::AbstractVector, fp::AbstractFlowpipe)
```

### Input

  * `d`  – direction
  * `fp` – flowpipe

### Output

The support function of the flowpipe along the given direction `d`.

### Notes

In this fallback implementation, the flowpipe behaves like the union of the reach-sets, i.e. the implementation is analogue to that of a `LazySet.UnionSetArray`.
