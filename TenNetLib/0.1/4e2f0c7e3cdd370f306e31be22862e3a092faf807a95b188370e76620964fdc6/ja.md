```
mutable struct StateEnvs{T <: Union{ProjMPO,
                              ProjMPO_MPS2,
                              ProjMPOSum2,
                              ProjMPOSum_MPS,
                              ProjCouplingModel,
                              ProjCouplingModel_MPS}
                        }
    psi::MPS
    PH::T
end
```

MPS状態`psi`とその環境`PH`を保持します。
