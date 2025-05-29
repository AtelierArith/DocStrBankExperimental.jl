```
mutable struct StateEnvsTTN{T1, T2 <: Union{EnvCouplingModelTTN,
                                            EnvCouplingModelProjTTN}}
    psi::TTN{T1}
    env::T{T2}
end
```

Holds the TTN and the environment.
