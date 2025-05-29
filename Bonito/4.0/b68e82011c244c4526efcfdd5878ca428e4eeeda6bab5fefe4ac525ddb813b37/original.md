```
Card(
    content;
    style::Styles=Styles(),
    backgroundcolor=RGBA(1, 1, 1, 0.2),
    shadow_size="0 4px 8px",
    padding="12px",
    margin="2px",
    shadow_color=RGBA(0, 0, 0.2, 0.2),
    width="auto",
    height="auto",
    border_radius="10px",
    div_attributes...,
)
```

A Card is a container with a shadow and rounded corners. It is a good way to group elements together and make them stand out from the background. One can easily style them via the above keyword arguments or via the `style` argument with any CSS attribute.

# Example

```@example
    App() do
        Card(
            DOM.h1("This is a card");
            width="200px",
            height="200px",
            backgroundcolor="white",
            shadow_size="0 0 10px",
            shadow_color="blue",
            padding="20px",
            margin="20px",
            border_radius="20px",
            style = Styles(
                CSS("hover", "background-color" => "lightgray")
            )
        )
    end

```
