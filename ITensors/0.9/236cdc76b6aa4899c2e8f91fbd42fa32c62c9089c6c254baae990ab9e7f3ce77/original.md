```
eachindval(i::Index)
```

Create an iterator whose values are Pairs of the form `i=>n` with `n` from `1:dim(i)`. This iterator is useful for accessing elements of an ITensor in a loop without needing to know the ordering of the indices. See also [`eachindval(is::Index...)`](@ref).
