```
sup(i::T) where T<:Real
```

Superscript notation for integers and rational numbers and *all* lowercase characters

#### Examples:

```
julia> sup(3) * 'P'
"³P"

julia> 'D' * sup(5//2)
"D₅⸝₂"

julia> 'D' * sub(50//20)
"D₅⸝₂"

julia> 'D' * sub(50//21)
"D₅₀⸝₂₁"
```

```
sup(str::String)
```

#### Example:

```
julia> 'D' * sup("superscript")
"Dˢᵘᵖᵉʳˢᶜʳⁱᵖᵗ"
```
