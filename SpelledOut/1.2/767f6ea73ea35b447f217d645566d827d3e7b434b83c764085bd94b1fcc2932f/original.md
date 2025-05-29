```julia
function spelled_out(
    number::Number;
    lang::Symbol = <locale language>,
    dict::Symbol = :modern
)
```

Spells out a number in words, in lowercase, given a specified language.  The default language is the one used on your system.  The `dict` keyword argument only applies to some languages; see "Supported Languages" in the docs for more information.

---

### Examples

```julia
julia> spelled_out(12, lang = :en)
"twelve"

julia> spelled_out(112, lang = :en)
"one hundred twelve"

julia> spelled_out(112, lang = :en_GB)
"one hundred and twelve"

julia> spelled_out(112, lang = :en, dict = :european)
"one hundred twelve"

julia> spelled_out(112, lang = :es)
"ciento doce"

julia> spelled_out(19, lang = :pt_BR)
"dezenove"

julia> spelled_out(19, lang = :pt)
"dezanove"
```
