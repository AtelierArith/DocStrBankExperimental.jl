```
none(::Type)::Option{T}
```

Construct the error value of `Option{T}`.

See also: [`Option`](@ref)

# Examples

```jldoctest
julia> none(String) === Option{String}(Err(nothing))
true

julia> none(Char) isa Option{Char}
true

julia> is_error(none(Char))
true

julia> convert(Option{Vector}, none) === none(Vector)
true
```
