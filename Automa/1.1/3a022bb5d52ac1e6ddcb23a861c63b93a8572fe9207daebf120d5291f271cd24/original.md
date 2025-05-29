```
tokenize(::Type{E}, data, version=1) -> Tokenizer
```

Create a `Tokenizer{E, typeof(data), version}`, iterating tokens of type `E` over `data`.

See also: [`Tokenizer`](@ref), [`make_tokenizer`](@ref), [`compile`](@ref)

# Examples

```jldoctest
julia> tokenize(UInt32, "hello")
Tokenizer{UInt32, String, 1}("hello")

julia> tokenize(Int8, [1, 2, 3], 3)
Tokenizer{Int8, Vector{Int64}, 3}([1, 2, 3])
```
