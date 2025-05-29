```
mutable struct ProjMPOSum_MPS
    PH::ProjMPOSum2
    pm::Vector{ProjMPS2}
    weight::Float64
end
```

Holds Environments from MPOs and MPSs.
