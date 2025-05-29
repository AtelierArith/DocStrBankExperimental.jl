```
undosmall(str::Union{Char, String})
```

通常のサイズの文字列にリセットします

例:

```
julia> undosmall("ˢᵘᵖᵉʳˢᶜʳⁱᵖᵗ")
"superscript"

julia> undosmall("⁻⁵ᐟ²")
"-5/2"

julia> undosmall("₋₅⸝₂")
"-5/2"
```
