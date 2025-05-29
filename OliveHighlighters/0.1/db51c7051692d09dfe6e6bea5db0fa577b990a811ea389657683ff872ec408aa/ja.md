```julia
style!(tm::TextStyleModifier, marks::Symbol, sty::Pair{String, String} ...) -> ::Nothing
style!(tm::TextStyleModifier, marks::Symbol, sty::Vector{Pair{String, String}}) -> ::Nothing
```

これらの `style!` バインディングは `OliveHighlighters` に属します。これらは `TextStyleModifier` の特定のクラスに対してスタイルを `sty` に設定します。

```julia
using OliveHighlighters

sample_str = "[key]"

hl = Highlighter(sample_str)

style!(hl, :key, "color" => "blue")

mark_between!(hl, "[", "]", :key)

string(hl)
```

  * 参照: `mark_all!`, `string(::TextStyleModifier)`, `clear!`, `set_text!`
