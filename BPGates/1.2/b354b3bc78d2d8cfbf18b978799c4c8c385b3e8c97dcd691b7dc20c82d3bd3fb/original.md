Apply coincidence measurement on a Bell state.

Return state and measurement result (`false` if an error is detected).

The measured state will be reset to 00.

```jldoctest
julia> bellmeasure!(BellState([0,1,1,1]), BellMeasure(2,1))
(BellState(Bool[0, 0, 1, 1]), false)
```
