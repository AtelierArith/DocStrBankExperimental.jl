```
order!(a::AbstractArray)
```

Given an array of tuples like that coming out of [`traverse!`](@ref), we sort by the `level`, strip the level out, and then retain unique entries. The aim of this function is to determine an optimal writing order when saving pattern data (although the GDSII spec does not require cells to be in a particular order, there may be performance ramifications).

For performance reasons, this function modifies `a` but what you want is the returned result array.
