A dropdown menu (`<select>`) - the user can choose one of the `options`, an array of `String`s.

See [`MultiSelect`](@ref) for a version that allows multiple selected items.

`options` can also be an array of pairs `key::Any => display_value::String`. The `key` is returned via `@bind`; the `display_value` is shown.

# Examples

`@bind veg Select(["potato", "carrot"])`

`@bind veg Select(["potato" => "🥔", "carrot" => "🥕"])`

`@bind veg Select(["potato" => "🥔", "carrot" => "🥕"], default="carrot")`

In all three cases, `veg` will be either `"potato"` or `"carrot"`.

The *key* can be any object, like a string, number, or even a function:

```julia
@bind f Select([cos => "cosine function", sin => "sine function"])

f(0.5)
```
