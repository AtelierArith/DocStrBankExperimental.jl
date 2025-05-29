```
GridArray{T,N,A,G,F,L,C,D,W} <: AbstractArray{T,N}
```

`N`-dimensional array of values of type `T` for each grid point using a struct-of-arrays like format that is GPU friendly.  Type `T` is assumed to be a hierarchical `struct` that can be `flatten`ed into an `NTuple{L,E<:Real}`.

The backing data array will be of type `A{E}` and will have the fields of `T` indexed via index `F`.

`GridArray` also stores values for the ghost cells of the grid which are accessible if `G==true`.
