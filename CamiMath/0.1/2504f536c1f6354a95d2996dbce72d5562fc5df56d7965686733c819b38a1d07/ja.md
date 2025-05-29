```
sub(i::T) where T<:Real
```

整数、有理数、および小文字の文字（'a', 'e', 'h', 'k', 'l', 'm', 'n', 'o', 'p', 'r', 's', 't', 'x'）の*部分集合*に対する添字表記

#### 例:

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

#### 例:

```
julia> "m" * sub("e")
"mₑ"

julia> 'D' * sub("50/21")
"D₅₀⸝₂₁"
```
