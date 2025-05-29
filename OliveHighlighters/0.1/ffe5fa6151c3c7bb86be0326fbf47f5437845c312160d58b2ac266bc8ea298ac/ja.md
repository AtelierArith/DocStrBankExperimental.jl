```julia
TextStyleModifier <: TextModifier
```

  * raw**::String**
  * taken**::Vector{Int64}**
  * marks**::Dict{UnitRange{Int64}, Symbol}**
  * styles**::Dict{Symbol, Vector{Pair{String, String}}}**

`TextStyleModifier`はテキストを解析し、そのスタイルを変更するために使用されます。この`Modifier`は、例えば`mark_all!`のような変更関数を通じて渡されます。`mark_all!`は、提供されたシンボルで全ての位置にマークを付け、その後`ToolipsServables.style!(tm, ::Symbol, pairs ...)`を使用してそれらのマークにスタイルを適用します。これらは`OliveHighlighters.classes`でリストされ、`ToolipsServables.remove!`で削除されます。`TextStyleModifier`は`Highlighter`としてもエイリアスされており、この型はエクスポートされますが、`TextStyleModifier`はエクスポートされません。

`OliveHighlighters`は、いくつかの事前構築されたハイライターを提供します：

  * `mark_toml!`
  * `toml_style!`
  * `mark_markdown!`
  * `markdown_style!`
  * `style_julia!`
  * `mark_julia!`
  * `julia_block!` < Juliaのためのハイライトとマークを組み合わせます。

`TextStyleModifier`のマークは`clear!`でクリアされますが、テキストが`set_text!`で設定されるときにも削除されます。最終結果を得るには、単に`TextStyleModifier`に対して`string`を呼び出します。

```julia
TextStyleModifier(::String = "")
```

例

```julia
using OliveHighlighters

tm = TextStyleModifier("function example(x::Any = 5) end")

OliveHighlighters.julia_block!(tm)

style!(tm, :default, "color" => "#333333")

display("text/html", string(tm))

# 再読み込み
set_text!(tm, "function sample end")

OliveHighlighters.mark_julia!(tm)

OliveHighlighters.mark_all(tm, "sample", :sample)
style!(tm, :sample, "color" => "red")
display("text/html", string(tm))
```

  * 参照：`classes`, `set_text!`, `julia_block!`, `mark_between!`
