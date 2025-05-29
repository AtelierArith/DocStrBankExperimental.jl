```
function StateEnvs(psi::MPS, H::MPO, Ms::Vector{MPS}; weight::Float64)
```

単一の `MPO` と励起状態 DMRG に使用される `MPS` のベクトルからの `StateEnvs` のコンストラクタです。
