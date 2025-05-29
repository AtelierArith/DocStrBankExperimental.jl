```julia
clear!(tm::TextStyleModifier) -> ::Nothing
```

`clear!` is used to remove the current set of `marks` from a `TextStyleModifier`.  This will allow for new marks to be loaded with a fresh call to a marking function. This      function is automatically called by `set_text!`, so unless we want to clear the marks without      changing the text, that would be the more convenient function to call.

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
