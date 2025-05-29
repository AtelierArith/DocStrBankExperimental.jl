```
mutable struct ProjMPO_MPS2
    PH::ProjMPO
    pm::Vector{ProjMPS2}
    weight::Float64
end
```

Holds Environments from MPO and MPS.
