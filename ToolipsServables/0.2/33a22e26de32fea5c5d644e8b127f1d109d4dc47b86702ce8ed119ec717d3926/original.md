```julia
remove!(cm::AbstractComponentModifier, s::Any) -> ::Nothing
```

`remove!` is a `ComponentModifier` `Function` that will remove a `Component`  from the page. `s` can be either a `String`, the component's `name` or the  `Component` itself.

```example
using Toolips
home = route("/") do c::Connection
    box = div("sample")
    style!(box, "margin" => 10px, "background-color" => "red")
    on(c, box, "click") do cl::ClientModifier
        remove!(cl, "sample")
    end
    write!(c, box)
end
```
