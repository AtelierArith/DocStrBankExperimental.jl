```
Ok(value::T) -> ok::Ok{T}
Ok{T}(value) -> ok::Ok{T}
Ok() -> Ok(nothing)
```

Indicate that `value` is a "success" in a sense defined by the API returning this value.

See also: [`isok`](@ref), [`unwrap`](@ref)

# Examples

```jldoctest Ok
julia> using Try

julia> result = Ok(1)
Try.Ok: 1

julia> Try.unwrap(result)
1
```
