`onchange(w::AbstractWidget, change = w[:changes])`

Return a widget that's identical to `w` but only updates on `change`. For a slider it corresponds to releasing it and for a textbox it corresponds to losing focus.

## Examples

```julia
sld = slider(1:100) |> onchange # update on release
txt = textbox("Write here") |> onchange # update on losing focus
```
