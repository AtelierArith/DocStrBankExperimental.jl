```
mutable struct StateEnvsTTN{T1, T2 <: Union{EnvCouplingModelTTN,
                                            EnvCouplingModelProjTTN}}
    psi::TTN{T1}
    env::T{T2}
end
```

TTNと環境を保持します。
