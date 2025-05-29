```julia
style!(cm::AbstractComponentModifier, name::Any, sty::Pair{String, <:Any} ...) -> ::Nothing
```

Styles `name` with the stylepairs `sty` in a callback. Note that `style!` will only add to the style,  whereas `set_style!` may be used to change the style. `name` should be a `Component` or a `Component`'s name.

```example
using Toolips
home = route("/") do c::Connection
    change = button("changer", text = "change text")
    on(change, "click") do cl::ClientModifier
        style!(cl, change, "background-color" => "green", "color" => "white")
    end
    write!(c, change)
end
```
