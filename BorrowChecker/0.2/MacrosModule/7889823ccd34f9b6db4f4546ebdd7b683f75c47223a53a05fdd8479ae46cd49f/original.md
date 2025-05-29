```
@&(T)
@&(:mut, T)
```

Type alias macro for borrowed types. `@& T` expands to `Union{T, Borrowed{T}}` and `@&(:mut, T)` expands to `Union{T, BorrowedMut{T}}` (as well as their `LazyAccessor` versions).

This is useful for writing generic signatures that accept either a raw value or a borrowed value.

# Examples

Here, we define a function that accepts a mutable borrow of a `Vector{Int}`. We also demonstrate the use of a [`Mutex`](@ref BorrowChecker.MutexModule.Mutex) to protect the vector.

```julia
julia> function foo(x::@&(:mut, Vector{Int}))
           push!(x, 4)
           return nothing
       end
foo (generic function with 1 method)

julia> m = Mutex([1, 2, 3])
Mutex{Vector{Int64}}([1, 2, 3])

julia> lock(m) do
           @ref_into :mut r = m[]
           foo(r)
       end

julia> println(m)
Mutex{Vector{Int64}}([1, 2, 3, 4])
```
