```
leq = initLinearEquationsIteration!(m::SimulationModel, leq_index::Int)
```

インデックス `leq_index` の線形方程式系の反復を初期化し、線形方程式系を構築して解くために while ループで使用できる参照を返します。
