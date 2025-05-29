```
function StateEnvs(psi::MPS, H::CouplingModel, Ms::Vector{MPS}; weight::Float64)
```

`CouplingModel` と励起状態 DMRG に使用される MPS のベクトルからの StateEnvs のコンストラクタ。`CouplingModel` の各項は並行して収束されます。
