```
Button(name; style=Styles(), dom_attributes...)
```

シンプルなボタンで、`style::Styles`でスタイルを設定できます。

### 例

```julia
App() do
    style = Styles(
        CSS("font-weight" => "500"),
        CSS(":hover", "background-color" => "silver"),
        CSS(":focus", "box-shadow" => "rgba(0, 0, 0, 0.5) 0px 0px 5px"),
    )
    button = Button("Click me"; style=style)
    on(button.value) do click::Bool
        @info "ボタンがクリックされました！"
    end
    return button
end

```
