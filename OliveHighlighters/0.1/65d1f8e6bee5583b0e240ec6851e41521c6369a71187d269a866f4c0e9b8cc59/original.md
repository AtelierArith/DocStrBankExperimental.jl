```julia
set_text!(tm::TextStyleModifier, s::String) -> ::String
```

Sets the text of a `TextStyleModifier`. This is an extra-convenient function,  it calls `rep_in` – an internal function used to replace client-side characters – and  sets the result as the text of `TextStyleModifier`, then it makes a call to `clear!` to clear the  current marks. This allows for the same highlighters with the same styles to be used with new text.

```julia
using OliveHighlighters
my_tm = Highlighter("function example() end")

OliveHighlighters.julia_block!(my_tm)

that_code = string(my_tm)

OliveHighlighters.set_text!(my_tm, "arg::Int64 = 5")

# julia_block! includes highlights, because we used `set_text!` we can remark the same highlighter:
OliveHighlighters.mark_julia!(my_tm)

new_code = string(my_tm)
```

  * See also: `clear!`, `Highlighter`, `classes`
