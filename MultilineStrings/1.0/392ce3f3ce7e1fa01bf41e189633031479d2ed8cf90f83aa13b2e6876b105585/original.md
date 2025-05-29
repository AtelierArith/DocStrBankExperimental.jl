```
indent(str::AbstractString, n::Int)
```

Indent each non-blank line by `n` spaces.

# Examples

```jldoctest; setup = :(using MultilineStrings)
julia> indent("a\nb", 4)
"    a\n    b"

julia> indent("  a\n  \n  b", 2)
"    a\n  \n    b"
```

See also `Base.unindent` and `Base.indentation`.
