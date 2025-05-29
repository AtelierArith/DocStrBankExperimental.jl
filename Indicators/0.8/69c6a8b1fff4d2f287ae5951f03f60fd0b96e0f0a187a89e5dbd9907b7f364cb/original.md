```
smi(hlc::Matrix{T}; n::Int64=13, nFast::Int64=2, nSlow::Int64=25, nSig::Int64=9,
    maFast::Function=ema, maSlow::Function=ema, maSig::Function=sma)::Matrix{Float64}
```

SMI (stochastic momentum oscillator)
