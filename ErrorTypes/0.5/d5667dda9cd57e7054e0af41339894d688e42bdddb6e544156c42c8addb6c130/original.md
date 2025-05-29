```
iter(x::Option)::OptionIterator
```

Produce an iterator over `x`, which yields the result value of `x` if `x` is some, or an empty iterator if it is none.

# Examples

```
julia> first(iter(some(19)))
19

julia> collect(iter(some("some string")))
1-element Vector{String}:
 "some string"

julia> isempty(iter(none(Dict)))
true

julia> collect(iter(none(Char)))
Char[]
```
