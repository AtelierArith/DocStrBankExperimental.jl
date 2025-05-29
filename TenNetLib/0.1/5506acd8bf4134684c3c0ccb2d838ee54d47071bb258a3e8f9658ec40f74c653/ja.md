```
function updateH!(sysenv::StateEnvs{ProjMPOSum2}, Hs::Vector{MPO}; recalcEnv::Bool = true)
```

`sysenv::StateEnvs`内のハミルトニアン`H`を更新します。`recalcEnv = false`はサポートされていません。
