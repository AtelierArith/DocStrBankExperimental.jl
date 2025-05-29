```
StylableSlider(
    range::AbstractVector;
    value=first(range),
    slider_height=15,
    thumb_width=slider_height,
    thumb_height=slider_height,
    track_height=slider_height / 2,
    track_active_height=track_height + 2,
    backgroundcolor="transparent",
    track_color="#eee",
    track_active_color="#ddd",
    thumb_color="#fff",
    style::Styles=Styles(),
    track_style::Styles=Styles(),
    thumb_style::Styles=Styles(),
    track_active_style::Styles=Styles(),
)
```

Creates a Stylable Slider, where the basic attributes are easily custimizable via keyword arguments, while the more advanced details can be styled via the `style`, `track_style`, `thumb_style` and `track_active_style` arguments with the whole might of CSS. This does not use `<input type="range">` but is a custom implementation using `<div>`s javascript, since it is not easily possible to style the native slider in a cross-browser way. For using pure HTML sliders, use `Bonito.Slider`.

# Example

```@example
App() do
    Bonito.StylableSlider(
        1:10;
        value=5,
        slider_height=20,
        track_color="lightblue",
        track_active_color="#F0F8FF",
        thumb_color="#fff",
        style=Styles(
            CSS("hover", "background-color" => "lightgray"),
            CSS("border-radius" => "0px"),
        ),
        track_style=Styles(
            "border-radius" => "3px",
            "border" => "1px solid black",
        ),
        thumb_style=Styles(
            "border-radius" => "3px",
            "border" => "1px solid black",
        ),
    )
end

```
