```julia
open_layer!(f::Function, con::AbstractContext, layer::String) -> ::Nothing
```

`open_layer` will open `layer` from `con`, providing each `Component` inside of that layer,  alongside its enumeration, to `f`. With this, functions such as `set!`, `set_gradient!`,  and additional `style!` dispatches can be used to make changes to entire layers – with some  dispatches, these layers are based on data and are able to further represent features.

```example

```
