```
contract!(C::AbstractTensorMap,
          A::AbstractTensorMap, (oindA, cindA)::Index2Tuple,
          B::AbstractTensorMap, (cindB, oindB)::Index2Tuple,
          (p₁, p₂)::Index2Tuple,
          α::Number, β::Number,
          backend, allocator)
```

更新された `C` を返します。これは、`A` と `B` のインデックスをそれぞれ `(oindA, cindA)` と `(cindB, oindB)` に従って入れ替えた後、`α * A * B` を `C` に加えた結果です。
