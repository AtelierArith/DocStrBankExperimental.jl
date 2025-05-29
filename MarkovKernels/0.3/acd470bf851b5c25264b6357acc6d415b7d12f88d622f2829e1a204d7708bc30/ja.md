```
compose(K2::AbstractMarkovKernel, K1::AbstractMarkovKernel)
```

K2 ∘ K1の合成であるK3を計算します。すなわち、

K3(y,x) = ∫ K2(y,z) K1(z,x) dz.

詳細は[`∘`](@ref)を参照してください。
