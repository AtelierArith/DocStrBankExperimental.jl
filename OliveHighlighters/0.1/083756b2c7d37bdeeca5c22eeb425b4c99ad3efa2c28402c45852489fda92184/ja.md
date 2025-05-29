#### OliveHighlighters

  * 2025年3月に[chifi](https://github.com/orgs/ChifiSource)によって作成されました。
  * このソフトウェアはMITライセンスです。

`OliveHighlighters`は、主に`Olive`パラメトリックノートブックエディタにサービスを提供することを意図して作成された`ToolipsServables`ベースのハイライトシステムです。このパッケージは、クリーンでインラインのスタイライズされた出力と宣言的な構文を明示的に提供し、将来の言語および構文仕様が`Olive`内で実装されるのを容易にすることを期待しています。言うまでもなく、このプロジェクトはさまざまな他の文脈でも役立つことが判明しています。

使用法は主に`Highlighter`または`TextStyleModifier`に関するもので、これらはスタイルでロードされ、次にマーク関数を通じて送信されてハイライトシステムを作成します。

```example
using OliveHighlighters

tm = TextStyleModifier("function example(x::Any = 5) end")

OliveHighlighters.julia_block!(tm)

style!(tm, :default, "color" => "#333333")

display("text/html", string(tm))

# 再読み込み時、スタイルは保存されます -- `julia_block!`の代わりに`mark_julia!`を呼び出します。
set_text!(tm, "function sample end")

OliveHighlighters.mark_julia!(tm)

OliveHighlighters.mark_all(tm, "sample", :sample)

style!(tm, :sample, "color" => "red")

display("text/html", string(tm))
```

##### 提供するもの

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
  * **マーク関数**
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

  * **含まれるハイライター**
  * `mark_julia!(tm::TextModifier)`
  * `style_julia!(tm::TextStyleModifier)`
  * `julia_block!(tm::TextStyleModifier)`
  * `mark_markdown!(tm::OliveHighlighters.TextModifier)`
  * `style_markdown!(tm::OliveHighlighters.TextStyleModifier)`
  * `mark_toml!(tm::OliveHighlighters.TextModifier)`
  * `style_toml!(tm::OliveHighlighters.TextStyleModifier)`
  * **内部**
  * `rep_in`
  * `rep_str`
