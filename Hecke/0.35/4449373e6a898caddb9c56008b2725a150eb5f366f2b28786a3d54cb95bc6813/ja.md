```
lift(a::T, K::PadicField) where T <: Union{Nemo.zzModRingElem, EuclideanRingResidueRingElem{ZZRingElem}, fpFieldElem} -> PadicFieldElem
```

剰余環からの要素のリフトを計算します。
