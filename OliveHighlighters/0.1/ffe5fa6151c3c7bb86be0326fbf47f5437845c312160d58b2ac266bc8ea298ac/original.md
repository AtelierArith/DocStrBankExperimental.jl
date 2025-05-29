```julia
TextStyleModifier <: TextModifier
```

  * raw**::String**
  * taken**::Vector{Int64}**
  * marks**::Dict{UnitRange{Int64}, Symbol}**
  * styles**::Dict{Symbol, Vector{Pair{String, String}}}**

The `TextStyleModifier` is used to lex text and change its style. This `Modifier` is passed through a mutating function, for example  `mark_all!`. `mark_all!` will mark all of the positions with the symbols we provide, then we use `ToolipsServables.style!(tm, ::Symbol, pairs ...)` to style  those marks. These can be listed with `OliveHighlighters.classes` and removed with `ToolipsServables.remove!`. The `TextStyleModifier` is also aliased as  `Highlighter`, and this type is exported whereas `TextStyleModifier` is not.

`OliveHighlighters` provides some pre-built highlighters:

  * `mark_toml!`
  * `toml_style!`
  * `mark_markdown!`
  * `markdown_style!`
  * `style_julia!`
  * `mark_julia!`
  * `julia_block!` < combines highlight and mark for Julia.

The `TextStyleModifier`'s marks are cleared with `clear!`, but are also removed when the text is set with `set_text!`. To get the final result, simply call  `string` on the `TextStyleModifier`.

```julia
TextStyleModifier(::String = "")
```

example

```julia
using OliveHighlighters

tm = TextStyleModifier("function example(x::Any = 5) end")

OliveHighlighters.julia_block!(tm)

style!(tm, :default, "color" => "#333333")

display("text/html", string(tm))

# reloading
set_text!(tm, "function sample end")

OliveHighlighters.mark_julia!(tm)

OliveHighlighters.mark_all(tm, "sample", :sample)
style!(tm, :sample, "color" => "red")
display("text/html", string(tm))
```

  * See also: `classes`, `set_text!`, `julia_block!`, `mark_between!`
