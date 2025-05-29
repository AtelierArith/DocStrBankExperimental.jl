```
none
```

Singleton instance of `ResultConstructor{Nothing, Err}(nothing)`. This value is useful because it can be `convert`ed to any `Option{T}`, giving the error value.

See also: [`Option`](@ref)

# Examples

```jldoctest
julia> f(x)::Option{Float64} = iszero(x) ? none : 1 / x;

julia> f(0)
none(Float64)

julia> struct MaybeInt32 x::Option{Int32} end;

julia> MaybeInt32(none)
MaybeInt32(none(Int32))
```
