#### OliveHighlighters

  * Created in March, 2025 by [chifi](https://github.com/orgs/ChifiSource)
  * This software is MIT-licensed.

`OliveHighlighters` is a `ToolipsServables`-based highlighting system created  primarily with the intention of serving the `Olive` parametric notebook  editor. This package explicitly provides clean, in-line stylized output and  declarative syntax in the hopes that this might make it easier for the future  language and syntax specifications to be implemeneted within `Olive`. Needless to say, this project turns out to also be useful in a variety of other  contexts.

Usage revolves primarily around the `Highlighter` or `TextStyleModifier`.  These are loaded with styles, and then sent through marking functions to  create the highlighting system.

```example
using OliveHighlighters

tm = TextStyleModifier("function example(x::Any = 5) end")

OliveHighlighters.julia_block!(tm)

style!(tm, :default, "color" => "#333333")

display("text/html", string(tm))

# reloading, the styles will be saved -- we call `mark_julia!` instead of `julia_block!`.
set_text!(tm, "function sample end")

OliveHighlighters.mark_julia!(tm)

OliveHighlighters.mark_all(tm, "sample", :sample)

style!(tm, :sample, "color" => "red")

display("text/html", string(tm))
```

##### provides

  * **Base**
  * `TextModifier`
  * `TextStyleModifier`
  * `Highlighter`
  * `classes`
  * `remove!`
  * `set_text!`
  * `clear!`
  * `style!(tm::TextStyleModifier, marks::Symbol, sty::Pair{String, String} ...)`
  * `style!(tm::TextStyleModifier, marks::Symbol, sty::Vector{Pair{String, String}}) = push!(tm.styles, marks => sty)`
  * `string(tm::TextStyleModifier; args ...)`
  * **marking functions**
  * `mark_all!(tm::TextModifier, s::String, label::Symbol)`
  * `mark_all!(tm::TextModifier, c::Char, label::Symbol)`
  * `mark_between!(tm::TextModifier, s::String, label::Symbol)`
  * `mark_between!(tm::TextModifier, s::String, s2::String, label::Symbol)`
  * `mark_before!(tm::TextModifier, s::String, label::Symbol;   until::Vector{String} = Vector{String}(), includedims_l::Int64 = 0,   includedims_r::Int64 = 0)`
  * `mark_after!(tm::TextModifier, s::String, label::Symbol;   until::Vector{String} = Vector{String}(), includedims_r::Int64 = 0,   includedims_l::Int64 = 0)`
  * `mark_inside!(f::Function, tm::TextModifier, label::Symbol)`
  * `mark_for!(tm::TextModifier, ch::String, f::Int64, label::Symbol)`
  * `mark*line*after!(tm::TextModifier, ch::String, label::Symbol) = mark_between!(tm, ch, "

", label)`

  * **included highlighters**
  * `mark_julia!(tm::TextModifier)`
  * `style_julia!(tm::TextStyleModifier)`
  * `julia_block!(tm::TextStyleModifier)`
  * `mark_markdown!(tm::OliveHighlighters.TextModifier)`
  * `style_markdown!(tm::OliveHighlighters.TextStyleModifier)`
  * `mark_toml!(tm::OliveHighlighters.TextModifier)`
  * `style_toml!(tm::OliveHighlighters.TextStyleModifier)`
  * **internal**
  * `rep_in`
  * `rep_str`
