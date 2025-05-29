```
PeriodicDistance2(mat::AbstractMatrix{T}) where T
```

Build a [`PeriodicDistance2`](@ref) object which can be called to compute squared periodic distances in a unit cell of given matrix `mat`.

!!! warning
    The `eltype` `T` of `mat` must be `isbitstype`, otherwise construction will fail. Convert your input to an appropriate type if need be.


!!! warning
    It is assumed that the unit cell is in standard settings: its angles must be above 60° or the returned distance may not be the shortest.

