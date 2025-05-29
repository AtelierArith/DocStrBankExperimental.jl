```
denest(S::MPolyRing, f::Union{PolyRingElem, MPolyRingElem})
```

Return an element of `S` resulting from denesting a element `f` of an iterated polynomial ring. The ring `S` should have the same base ring and number of variables as `denest(parent(f))`.
