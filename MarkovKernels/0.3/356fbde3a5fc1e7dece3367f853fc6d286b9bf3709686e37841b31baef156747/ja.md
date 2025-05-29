```
compose(L2::AbstractLikelihood, L1::AbstractLiklelihood)
```

L2 ∘ L1の合成L3を計算します。すなわち、

L3(x) = L1(x) * L2(x)

詳細は[`∘`](@ref)を参照してください。
