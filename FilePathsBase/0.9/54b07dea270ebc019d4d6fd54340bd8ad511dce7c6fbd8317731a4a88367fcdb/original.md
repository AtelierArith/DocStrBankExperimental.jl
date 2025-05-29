*(a::T, b::Union{T, AbstractString, AbstractChar}...) where {T <: AbstractPath} -> T

Concatenate paths, strings and/or characters, producing a new path. This is equivalent to concatenating the string representations of paths and other strings and then constructing a new path.

# Example

```jldoctest
julia> p"foo" * "bar"
p"foobar"
```
