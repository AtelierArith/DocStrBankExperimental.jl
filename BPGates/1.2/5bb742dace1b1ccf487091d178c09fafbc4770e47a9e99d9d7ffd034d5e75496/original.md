`PauliNoiseOp(idx,px,py,pz)` causes qubit-pair `idx` to flip to one of the other 3 Bell states with probabilities `px`, `py`, `pz` respectively.

```jldoctest
julia> apply!(BellState([0,0]), PauliNoiseOp(1,1,0,0))
BellState(Bool[0, 1])

julia> apply!(BellState([0,0]), PauliNoiseOp(1,0,1,0))
BellState(Bool[1, 1])

julia> apply!(BellState([0,0]), PauliNoiseOp(1,0,0,1))
BellState(Bool[1, 0])
```
