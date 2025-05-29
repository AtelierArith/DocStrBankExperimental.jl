```
Dropdown(options; index=1, option_to_string=string, style=Styles(), dom_attributes...)
```

スタイルを `style::Styles` 属性を介して設定できるシンプルなドロップダウン。

### 例

```julia
App() do
    style = Styles(
        CSS("font-weight" => "500"),
        CSS(":hover", "background-color" => "silver"),
        CSS(":focus", "box-shadow" => "rgba(0, 0, 0, 0.5) 0px 0px 5px"),
    )
    dropdown = Dropdown(["a", "b", "c"]; index=2, style=style)
    on(dropdown.value) do value
        @info value
    end
    return dropdown
end

```
