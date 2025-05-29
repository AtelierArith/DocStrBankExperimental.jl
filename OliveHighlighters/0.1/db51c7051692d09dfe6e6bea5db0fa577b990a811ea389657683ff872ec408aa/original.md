```julia
style!(tm::TextStyleModifier, marks::Symbol, sty::Pair{String, String} ...) -> ::Nothing
style!(tm::TextStyleModifier, marks::Symbol, sty::Vector{Pair{String, String}}) -> ::Nothing
```

These `style!` bindings belong to `OliveHighlighters`.These will set the style for a particular class on a `TextStyleModifier` to `sty`.

```julia
using OliveHighlighters

sample_str = "[key]"

hl = Highlighter(sample_str)

style!(hl, :key, "color" => "blue")

mark_between!(hl, "[", "]", :key)

string(hl)
```

  * See also: `mark_all!`, `string(::TextStyleModifier)`, `clear!`, `set_text!`
