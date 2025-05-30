```
@eponymargs(a, b::T, ...)
```

Expands to form like `((a, b)::NamedTuple{(:a, :b), <: Tuple{Any, T}})`, using the variable names *both* for the `NamedTuple` and deconstruction in the function arguments.

Valid arguments are variable names, or names followed by a type specifier (when missing, `Any` is used).

# Example

```jldoctest
julia> using EponymTuples

julia> foo(@eponymargs(a, b)) = a + b
foo (generic function with 1 method)

julia> foo((a = 1, b = 2))
3
```
