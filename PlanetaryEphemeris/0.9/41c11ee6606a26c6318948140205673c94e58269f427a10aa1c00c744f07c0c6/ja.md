```
nbodyind(N::Int, i::Int)
nbodyind(N::Int, ivec::AbstractVector{Int})
```

`i`-番目の物体（または`ivec`-番目の物体）の位置と速度のインデックスを、`N`個の物体を持つベクトルで返します。この関数は、ベクトルが次の形式であると仮定します：`3N`の位置 + `3N`の速度 (+ 月の物理的リブラション + TT-TDB)。
