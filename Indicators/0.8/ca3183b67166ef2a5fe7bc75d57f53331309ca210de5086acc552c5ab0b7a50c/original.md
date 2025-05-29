```
kst(x::Array{T};
    nroc::Array{Int64}=[10,15,20,30], navg::Array{Int64}=[10,10,10,15],
    wgts::Array{Int64}=collect(1:length(nroc)), ma::Function=sma)::Array{Float64}

```

KST (Know Sure Thing) – smoothed and summed rates of change
