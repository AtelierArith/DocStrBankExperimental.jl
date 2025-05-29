```
known(T::Type)
```

Returns the known value corresponding to a static type `T`. If `T` is not a static type then `nothing` is returned.

`known` ensures that the type of the returned value is always inferred, even if the compiler fails to infer the exact value.

See also: [`static`](@ref), [`is_static`](@ref), [`dynamic`](@ref)

# Examples

```julia
julia> known(StaticInt{1})
1

julia> known(Int)

```
