```
interreduce!(g::Vector{FreeAssociativeAlgebraElem{T}}) where T
```

Interreduce a given Groebner basis with itself, i.e. compute the normal form of each element of `g` with respect to the rest of the elements and discard elements with normal form $0$ and duplicates.
