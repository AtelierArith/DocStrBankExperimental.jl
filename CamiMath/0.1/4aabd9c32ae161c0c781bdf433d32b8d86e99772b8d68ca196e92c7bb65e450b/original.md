```
undosup(str::Union{Char, String})
```

Undo conversion of Integer or Rational{Int} to superscript String Examples:

```
julia> undosup("⁻⁵ᐟ²")
-5//2
```
