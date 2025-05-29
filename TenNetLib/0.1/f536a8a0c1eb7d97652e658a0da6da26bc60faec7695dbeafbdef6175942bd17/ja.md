```
mutable struct ProjCouplingModel_MPS
    PH::ProjCouplingModel
    pm::Vector{ProjMPS2}
    weight::Float64
end
```

CouplingModelとMPSからの環境を保持します。
