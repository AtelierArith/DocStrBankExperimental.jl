```
NumberInput(default_value; style=Styles(), dom_attributes...)
```

スタイルを `style::Styles` 属性を介して設定できるシンプルな NumberInput。

### 例

```julia
App() do
    style = Styles(
        CSS("font-weight" => "500"),
        CSS(":hover", "background-color" => "silver"),
        CSS(":focus", "box-shadow" => "rgba(0, 0, 0, 0.5) 0px 0px 5px"),
    )
    numberinput = NumberInput(0.0; style=style)
    on(numberinput.value) do value::Float64
        @info value
    end
    return numberinput
end

```
