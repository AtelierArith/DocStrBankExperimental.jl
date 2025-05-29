```
sub(i::T) where T<:Real
```

Subscript notation for integers, rational numbers and a *subset* of lowercase  characters ('a', 'e', 'h', 'k', 'l', 'm', 'n', 'o', 'p', 'r', 's', 't', 'x')

#### Examples:

```
julia> 'D' * sub(5//2)
"D₅⸝₂"

julia> 'D' * sub(50//20)
"D₅⸝₂"

julia> 'D' * sub(50//21)
"D₅₀⸝₂₁"
```

```
sub(str::String)
```

#### Example:

```
julia> "m" * sub("e")
"mₑ"

julia> 'D' * sub("50/21")
"D₅₀⸝₂₁"
```
