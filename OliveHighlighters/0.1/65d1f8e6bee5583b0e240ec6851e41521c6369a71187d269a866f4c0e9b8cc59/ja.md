```julia
set_text!(tm::TextStyleModifier, s::String) -> ::String
```

`TextStyleModifier`のテキストを設定します。これは非常に便利な関数で、クライアント側の文字を置き換えるために使用される内部関数`rep_in`を呼び出し、その結果を`TextStyleModifier`のテキストとして設定し、現在のマークをクリアするために`clear!`を呼び出します。これにより、同じスタイルのハイライターを新しいテキストで使用することができます。

```julia
using OliveHighlighters
my_tm = Highlighter("function example() end")

OliveHighlighters.julia_block!(my_tm)

that_code = string(my_tm)

OliveHighlighters.set_text!(my_tm, "arg::Int64 = 5")

# julia_block! はハイライトを含みます。`set_text!`を使用したため、同じハイライターを再マークできます：
OliveHighlighters.mark_julia!(my_tm)

new_code = string(my_tm)
```

  * 参照: `clear!`, `Highlighter`, `classes`
