```
mutable struct ProjMPOSum_MPS
    PH::ProjMPOSum2
    pm::Vector{ProjMPS2}
    weight::Float64
end
```

MPOとMPSから環境を保持します。
