`@manipulate expr`

The @manipulate macro lets you play with any expression using widgets. `expr` needs to be a `for` loop. The `for` loop variable are converted to widgets using the [`widget`](@ref) function (ranges become `slider`, lists of options become `togglebuttons`, etc...). The `for` loop body is displayed beneath the widgets and automatically updated as soon as the widgets change value.

Use `throttle = df` to only update the output after a small time interval `dt` (useful if the update is costly as it prevents multiple updates when moving for example a slider).

## Examples

```julia
using Colors

@manipulate for r = 0:.05:1, g = 0:.05:1, b = 0:.05:1
    HTML(string("<div style='color:#", hex(RGB(r,g,b)), "'>Color me</div>"))
end

@manipulate throttle = 0.1 for r = 0:.05:1, g = 0:.05:1, b = 0:.05:1
    HTML(string("<div style='color:#", hex(RGB(r,g,b)), "'>Color me</div>"))
end
```

[`@layout!`](@ref) can be used to adjust the layout of a manipulate block:

```julia
using Interact

ui = @manipulate throttle = 0.1 for r = 0:.05:1, g = 0:.05:1, b = 0:.05:1
    HTML(string("<div style='color:#", hex(RGB(r,g,b)), "'>Color me</div>"))
end
@layout! ui dom"div"(observe(_), vskip(2em), :r, :g, :b)
ui
```
