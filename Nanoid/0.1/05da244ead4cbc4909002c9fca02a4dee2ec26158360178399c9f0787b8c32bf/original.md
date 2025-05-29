```
nanoid(size::Integer = 21; alphabet::String = "") -> String
```

Generate a random Nanoid with the given size and alphabet. Size defaults to 21, and alphabet defaults to the URL-safe alphabet.

## Examples

```jldoctest
julia> nanoid()
"tcDIFxMJHw6UgUnbI_6za"

julia> nanoid(10)
"OutzQWa1SB"

julia> nanoid(; alphabet = "ABCDEFGHIJ")
"GEHCAGFJIAHCJGIHHIHFF"

julia> nanoid(10; alphabet = "abcdef")
"abeafebaab"
```
