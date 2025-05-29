```
mutable struct EnvCouplingModelProjTTN
    env_tensors::LinkTensorsTTN
    proj_tensors::Vector{LinkProjTTN}
    weight::Float64
end
```

A wrapper to hold `LinkTensorsTTN` and a vector of `LinkProjTTN`.
