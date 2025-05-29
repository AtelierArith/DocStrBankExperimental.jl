```
TextField(default_text; style=Styles(), dom_attributes...)
```

A simple TextField, which can be styled via the `style::Styles` attribute.

### Example

```julia
App() do
    style = Styles(
        CSS("font-weight" => "500"),
        CSS(":hover", "background-color" => "silver"),
        CSS(":focus", "box-shadow" => "rgba(0, 0, 0, 0.5) 0px 0px 5px"),
    )
    textfield = TextField("write something"; style=style)
    on(textfield.value) do text::String
        @info text
    end
    return textfield
end

```
