```
mutable struct ProjCouplingModel
    lpos::Int
    rpos::Int
    nsite::Int
    M::CouplingModel
    LR::Vector{IDTensors}
end
```

Holds Environments from CouplingModel.
