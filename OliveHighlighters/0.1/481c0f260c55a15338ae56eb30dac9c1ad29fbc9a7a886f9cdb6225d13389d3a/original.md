```julia
remove!(tm::TextStyleModifier, key::Symbol)
```

Removes a given style string from a `TextStyleModifier`

```julia
using OliveHighlighters; TextStyleModifier, style_julia!
tm = TextStyleModifier("")
style_julia!(tm)

# check classes:
classes(tm)

# remove class:
remove!(tm, :default)
```

  * See also: `set_text!`, `TextStyleModifier`, `clear!`
