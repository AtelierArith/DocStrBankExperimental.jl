```
lift(a::T, K::PadicField) where T <: Union{Nemo.zzModRingElem, EuclideanRingResidueRingElem{ZZRingElem}, fpFieldElem} -> PadicFieldElem
```

Computes a lift of the element from the residue ring.
