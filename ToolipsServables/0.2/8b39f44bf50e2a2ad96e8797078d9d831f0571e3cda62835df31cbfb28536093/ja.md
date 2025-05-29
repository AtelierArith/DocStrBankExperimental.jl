```julia
set_text!(c::AbstractComponentModifier, s::Any, txt::Any) -> ::Nothing
```

`Component`（または `Component` `name`）`s`のテキストを設定します。`txt`は`Component{:property}`でも構いません。

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
