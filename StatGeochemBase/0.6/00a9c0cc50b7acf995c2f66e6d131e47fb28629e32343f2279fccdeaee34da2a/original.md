```julia
containsi(haystack, needle)
```

Converts both `haystack` and `needle` to strings and checks whether `string(haystack)` contains `string(needle)`, ignoring case.

### Examples

```julia
julia> containsi("QuickBrownFox", "brown")
true
```
