```julia
style!(cm::AbstractComponentModifier, name::Any, sty::Pair{String, <:Any} ...) -> ::Nothing
```

`name`をスタイルペア`sty`でコールバック内でスタイル設定します。`style!`はスタイルを追加するだけであり、`set_style!`はスタイルを変更するために使用されることに注意してください。`name`は`Component`または`Component`の名前である必要があります。

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
