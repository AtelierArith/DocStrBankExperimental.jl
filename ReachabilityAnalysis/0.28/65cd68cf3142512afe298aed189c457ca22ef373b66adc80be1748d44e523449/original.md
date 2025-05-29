```
set(fp::AbstractFlowpipe)
```

Return the geometric set represented by this flowpipe as the union of reach-sets.

### Input

  * `fp`  – flowpipe

### Output

The set union of the array of reach-sets of the flowpipe.

## Notes

To retrieve the array of sets stored in the flowpipe use `array(fp)`. To get a set at a particular index, use `set(F[ind])` or `set(F, ind)`.
