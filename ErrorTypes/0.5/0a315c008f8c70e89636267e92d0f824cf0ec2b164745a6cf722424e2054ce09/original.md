```
base(x::Option{T})
```

Convert an `Option{T}` to a `Union{Some{T}, Nothing}`.

See also: [`Option`](@ref)

# Examples

```jldoctest
julia> sub_nonneg(x::Int)::Option{Int} = x < 1 ? none : some(x - 1);

julia> base(sub_nonneg(-3)) === nothing
true

julia> base(sub_nonneg(2))
Some(1)
```
