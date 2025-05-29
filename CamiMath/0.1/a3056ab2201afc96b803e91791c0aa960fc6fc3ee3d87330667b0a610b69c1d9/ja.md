```
sup(i::T) where T<:Real
```

整数と有理数のための上付き文字表記と*すべての*小文字

#### 例:

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

#### 例:

```
julia> 'D' * sup("superscript")
"Dˢᵘᵖᵉʳˢᶜʳⁱᵖᵗ"
```
