`PauliNoiseOp(idx,px,py,pz)` は、量子ビットペア `idx` を他の3つのベル状態のいずれかに、確率 `px`, `py`, `pz` でフリップさせます。

```jldoctest
julia> apply!(BellState([0,0]), PauliNoiseOp(1,1,0,0))
BellState(Bool[0, 1])

julia> apply!(BellState([0,0]), PauliNoiseOp(1,0,1,0))
BellState(Bool[1, 1])

julia> apply!(BellState([0,0]), PauliNoiseOp(1,0,0,1))
BellState(Bool[1, 0])
```
