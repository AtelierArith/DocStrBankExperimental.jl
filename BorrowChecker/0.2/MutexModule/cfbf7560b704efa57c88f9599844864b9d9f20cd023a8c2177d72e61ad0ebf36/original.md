```
Mutex{T} <: AbstractMutex{T}
```

A mutex that protects a value of type T. Provides safe concurrent access to the protected value.

# Example

```julia
m = Mutex([1, 2, 3])
lock(m)
@ref_into :mut arr = m[]
push!(arr, 4)
unlock(m)
```
