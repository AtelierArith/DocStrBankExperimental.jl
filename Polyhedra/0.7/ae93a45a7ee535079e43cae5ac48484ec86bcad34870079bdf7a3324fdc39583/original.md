```
dim(h::HRep, current=false)
```

Returns the dimension of the affine hull of the polyhedron. That is the number of non-redundant hyperplanes that define it. If `current` is `true` then it simply returns the dimension according the current number of hyperplanes, assuming that the H-linearity has already been detected. Otherwise, it first calls [`detecthlinearity!`](@ref).
