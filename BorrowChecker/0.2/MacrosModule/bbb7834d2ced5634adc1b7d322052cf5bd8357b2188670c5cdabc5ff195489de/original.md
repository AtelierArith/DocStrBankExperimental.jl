```
@ref_into [:mut] var = mutex[]
```

Create a reference to the protected value in a mutex.

If `:mut` is specified, creates a mutable reference. Otherwise, creates an immutable reference.

# Examples

```julia
m = Mutex([1, 2, 3])
lock(m) do
    @ref_into :mut arr2 = m[]
    push!(arr2, 4)
end
```
