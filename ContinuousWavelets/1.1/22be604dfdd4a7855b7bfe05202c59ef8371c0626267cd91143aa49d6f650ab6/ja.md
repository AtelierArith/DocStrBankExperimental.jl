```
computeWavelets(n1::Integer, c::CWT{B,CT,W}; T = Float64, space = false) where {B<:WaveletBoundary,W,CT} -> daughters, ω
```

変換に使用されるウェーブレットを事前計算します。詳細については、cwtを参照してください。
