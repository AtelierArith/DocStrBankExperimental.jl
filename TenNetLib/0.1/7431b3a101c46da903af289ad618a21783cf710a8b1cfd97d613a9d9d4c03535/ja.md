```
mutable struct EnvCouplingModelProjTTN
    env_tensors::LinkTensorsTTN
    proj_tensors::Vector{LinkProjTTN}
    weight::Float64
end
```

`LinkTensorsTTN` と `LinkProjTTN` のベクターを保持するラッパーです。
