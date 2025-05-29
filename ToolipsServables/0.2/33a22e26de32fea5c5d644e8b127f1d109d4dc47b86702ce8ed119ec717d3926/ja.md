```julia
remove!(cm::AbstractComponentModifier, s::Any) -> ::Nothing
```

`remove!` は `ComponentModifier` の `Function` で、ページから `Component` を削除します。`s` は `String`、コンポーネントの `name`、または `Component` 自体のいずれかです。

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
