```
mutable struct ProjCouplingModel_MPS
    PH::ProjCouplingModel
    pm::Vector{ProjMPS2}
    weight::Float64
end
```

Holds Environments from CouplingModel and MPS.
