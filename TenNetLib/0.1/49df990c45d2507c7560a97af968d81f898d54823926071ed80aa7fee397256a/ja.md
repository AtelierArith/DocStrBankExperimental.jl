```
function StateEnvsTTN(psi::TTN, H::CouplingModel, Ms::Vector{TTN}; weight::Float64)
```

`CouplingModel` と励起状態探索に使用される TTN のベクトルからの StateEnvsTTN のコンストラクタ。`CouplingModel` の各項は並行して収束されます。
