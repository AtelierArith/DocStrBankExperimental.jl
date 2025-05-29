Charがヘブライ語の母音記号である場合はtrueです。

**例**

```julia
julia> is_vowelpoint('א')
false

julia> is_vowelpoint(BiblicalHebrew.qamats_ch)
true
```

```julia
is_vowelpoint(c)

```
