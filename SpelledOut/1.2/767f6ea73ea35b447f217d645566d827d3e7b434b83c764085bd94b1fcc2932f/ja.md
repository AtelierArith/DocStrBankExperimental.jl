```julia
function spelled_out(
    number::Number;
    lang::Symbol = <locale language>,
    dict::Symbol = :modern
)
```

指定された言語で、数を小文字の単語で表記します。デフォルトの言語は、システムで使用されているものです。`dict`キーワード引数は、一部の言語にのみ適用されます。詳細については、ドキュメントの「サポートされている言語」を参照してください。

---

### 例

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
