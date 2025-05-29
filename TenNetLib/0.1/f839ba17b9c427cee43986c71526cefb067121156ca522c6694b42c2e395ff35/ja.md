```
function StateEnvs(psi::MPS, Hs::Vector{MPO}, Ms::Vector{MPS}; weight::Float64)
```

`MPO`のベクトルと`MPS`のベクトルからの`StateEnvs`のコンストラクタで、励起状態DMRGに使用されます。`MPO`の環境は並行して収束されます。
