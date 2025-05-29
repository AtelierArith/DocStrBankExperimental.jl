```julia
clear!(tm::TextStyleModifier) -> ::Nothing
```

`clear!` は `TextStyleModifier` から現在の `marks` のセットを削除するために使用されます。これにより、新しいマークをマーク関数への新しい呼び出しで読み込むことができます。この関数は `set_text!` によって自動的に呼び出されるため、テキストを変更せずにマークをクリアしたい場合は、それがより便利な関数になります。

```julia
using OliveHighlighters
my_tm = Highlighter("function example() end")

OliveHighlighters.julia_block!(my_tm)

that_code = string(my_tm)

# avoiding `set_text!`
OliveHighlighters.clear!(my_tm)
my_tm.raw = "function sample()\n x = 5 \nend"

# julia_block! includes highlights, because we used `set_text!` we can remark the same highlighter:
OliveHighlighters.mark_julia!(my_tm)

new_code = string(my_tm)
```

  * See also: `set_text!`, `style!`
