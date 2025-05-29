```
mutable struct ProjCouplingModel
    lpos::Int
    rpos::Int
    nsite::Int
    M::CouplingModel
    LR::Vector{IDTensors}
end
```

CouplingModelからの環境を保持します。
