True if a Char is a vowel point, a consonant, or one of the Unicode combining characters that are part of writing consonantal values.

**Examples**

```julia
julia> is_alphabetic('א')
true

julia> is_alphabetic(BiblicalHebrew.qamats_ch)
true
```

```julia
is_alphabetic(c)

```
