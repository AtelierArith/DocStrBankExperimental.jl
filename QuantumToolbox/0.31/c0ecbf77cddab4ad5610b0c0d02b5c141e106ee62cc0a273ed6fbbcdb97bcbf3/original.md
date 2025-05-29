```
size(A::AbstractQuantumObject)
size(A::AbstractQuantumObject, idx::Int)
shape(A::AbstractQuantumObject)
shape(A::AbstractQuantumObject, idx::Int)
```

Returns a tuple containing each dimensions of the array in the [`AbstractQuantumObject`](@ref).

Optionally, you can specify an index (`idx`) to just get the corresponding dimension of the array.

!!! note
    `shape` is a synonym of `size`.

