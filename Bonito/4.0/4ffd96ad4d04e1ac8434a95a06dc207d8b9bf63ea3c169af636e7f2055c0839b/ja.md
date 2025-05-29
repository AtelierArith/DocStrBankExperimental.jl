```
TextField(default_text; style=Styles(), dom_attributes...)
```

スタイルを `style::Styles` 属性を介して設定できるシンプルな TextField です。

### 例

```julia
App() do
    style = Styles(
        CSS("font-weight" => "500"),
        CSS(":hover", "background-color" => "silver"),
        CSS(":focus", "box-shadow" => "rgba(0, 0, 0, 0.5) 0px 0px 5px"),
    )
    textfield = TextField("何かを書く"; style=style)
    on(textfield.value) do text::String
        @info text
    end
    return textfield
end

```
