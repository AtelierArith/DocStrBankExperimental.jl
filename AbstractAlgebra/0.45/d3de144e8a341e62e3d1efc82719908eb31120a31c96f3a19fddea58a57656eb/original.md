```
quo(R::Ring, a::RingElement; cached::Bool = true)
```

Returns `S, f` where `S = residue_ring(R, a)` and `f` is the  projection map from `R` to `S`. This map is supplied as a map with section where the section is the lift of an element of the residue field back to the ring `R`.
