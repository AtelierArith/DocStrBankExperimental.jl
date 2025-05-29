```
renest(R::Union{PolyRing, MPolyRing}, g::MPolyRingElem)
```

Return an element of iterated polynomial ring `R` from its denested counterpart. The return satisfies `f == renest(R, denest(denest(R), f))`.
