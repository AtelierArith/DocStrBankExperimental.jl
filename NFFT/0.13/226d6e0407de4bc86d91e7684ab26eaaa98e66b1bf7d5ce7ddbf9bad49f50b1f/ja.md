```
    plan_nfft(k::Matrix{T}, N::NTuple{D,Int}, rest...;  kargs...)
```

サイズ`N`の配列のNFFTを、`k`に含まれるノードで計算するプランを作成します。
