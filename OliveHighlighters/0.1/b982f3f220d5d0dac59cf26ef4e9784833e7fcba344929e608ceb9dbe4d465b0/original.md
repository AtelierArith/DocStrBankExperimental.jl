```julia
classes(tm::TextStyleModifier) -> Base.Generator
```

Returns a `Tuple` generator for the classes currently styled in the `TextStyleModifier`. This      is equivalent of getting the keys of the `styles` field. `remove!` can also be used to remove classes.      (To allocate the generator simply provide it to a `Vector`)

```julia
using OliveHighlighters; TextStyleModifier, style_julia!
tm = TextStyleModifier("")
style_julia!(tm)

classes(tm)

# allocated:
my_classes = [classes(tm) ...]
```

  * See also: `set_text!`, `TextStyleModifier`, `clear!`, `remove!(tm::TextStyleModifier, key::Symbol)`
