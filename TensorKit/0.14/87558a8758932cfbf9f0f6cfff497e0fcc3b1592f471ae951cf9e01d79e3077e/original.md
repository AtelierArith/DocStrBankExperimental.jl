```
contract!(C::AbstractTensorMap,
          A::AbstractTensorMap, (oindA, cindA)::Index2Tuple,
          B::AbstractTensorMap, (cindB, oindB)::Index2Tuple,
          (p₁, p₂)::Index2Tuple,
          α::Number, β::Number,
          backend, allocator)
```

Return the updated `C`, which is the result of adding `α * A * B` to `C` after permuting the indices of `A` and `B` according to `(oindA, cindA)` and `(cindB, oindB)` respectively.
