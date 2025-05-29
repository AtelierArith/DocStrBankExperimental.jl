`widget(args...; kwargs...)`

Automatically convert Julia types into appropriate widgets. `kwargs` are passed to the more specific widget function.

## Examples

```julia
map(display, [
    widget(1:10),                 # Slider
    widget(false),                # Checkbox
    widget("text"),               # Textbox
    widget(1.1),                  # Spinbox
    widget([:on, :off]),          # Toggle Buttons
    widget(Dict("π" => float(π), "τ" => 2π)),
    widget(colorant"red"),        # Color picker
    widget(Dates.today()),        # Date picker
    widget(Dates.Time()),         # Time picker
    ]);
```
