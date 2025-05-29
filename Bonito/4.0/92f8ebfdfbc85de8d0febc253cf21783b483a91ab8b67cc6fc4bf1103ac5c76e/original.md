```
Labeled(object, label; label_style=Styles(), attributes...)
```

A Labeled container with a simople layout to put a label next to an object.

```@example
App() do
    label_style = Styles(
        "color" => "white",
        "padding" => "3px",
        "font-size" => "1.5rem",
        "text-shadow" => "0px 0px 10px black, 1px 1px 3px black")
    slider = StylableSlider(1:10)
    Card(Labeled(slider, slider.value; label_style=label_style, width="auto"); backgroundcolor="gray")
end

```
