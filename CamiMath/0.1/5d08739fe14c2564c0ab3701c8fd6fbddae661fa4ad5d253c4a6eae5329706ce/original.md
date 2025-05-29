```
undosmall(str::Union{Char, String})
```

Reset to normal size String

Examples:

```
julia> undosmall("ˢᵘᵖᵉʳˢᶜʳⁱᵖᵗ")
"superscript"

julia> undosmall("⁻⁵ᐟ²")
"-5/2"

julia> undosmall("₋₅⸝₂")
"-5/2"
```
