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

Holds the MPS state `psi` and its environments `PH`.
