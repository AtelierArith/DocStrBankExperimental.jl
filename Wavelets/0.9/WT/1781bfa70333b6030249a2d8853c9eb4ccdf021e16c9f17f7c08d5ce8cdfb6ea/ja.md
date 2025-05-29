```
  (daughters, ω) = computeWavelets(n1::Integer, c::CFW{W}; T=Float64, J1::Int64=-1, dt::S=NaN, s0::V=NaN) where {S<:Real,
                                                               W<:WT.WaveletBoundary, V}
```

は、変換 c::CFW{W} で使用されるウェーブレットを事前計算するだけです。詳細については cwt を参照してください。
