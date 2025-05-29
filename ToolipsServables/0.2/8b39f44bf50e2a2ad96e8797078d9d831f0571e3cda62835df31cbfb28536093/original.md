```julia
set_text!(c::AbstractComponentModifier, s::Any, txt::Any) -> ::Nothing
```

Sets the text of the `Component` (or `Component` `name`) `s`. `txt` can also be a `Component{:property}`

```example
using Toolips
home = route("/") do c::Connection
    mytextbox = div("sampletext", text = "text will change", align = "center")
    changetxt = button("changer", text = "change text", align = "center")
    on(changetxt, "click") do cl::ClientModifier
        set_text!(cl, mytextbox, "text changed!")
    end
    write!(c, mytextbox, changetxt)
end
```
