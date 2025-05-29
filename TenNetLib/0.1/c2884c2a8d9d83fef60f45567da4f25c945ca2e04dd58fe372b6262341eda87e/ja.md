```
mutable struct ProjMPO_MPS2
    PH::ProjMPO
    pm::Vector{ProjMPS2}
    weight::Float64
end
```

MPOとMPSから環境を保持します。
