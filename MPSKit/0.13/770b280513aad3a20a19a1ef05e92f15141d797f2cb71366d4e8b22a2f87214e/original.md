```
PeriodicArray{T,N} <: AbstractArray{T,N}
```

Array wrapper with periodic boundary conditions.

# Fields

  * `data::Array{T,N}`: the data of the array

# Examples

```jldoctest
A = PeriodicArray([1, 2, 3])
A[0], A[2], A[4]

# output

(3, 2, 1)
```

```jldoctest
A = PeriodicArray([1 2; 3 4])
A[-1, 1], A[1, 1], A[4, 5]

# output

(1, 1, 3)
```

See also [`PeriodicVector`](@ref), [`PeriodicMatrix`](@ref)
