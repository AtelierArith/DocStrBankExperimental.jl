```
function change_value(widget::WidgetProgressBar, new_value::Integer; color::Int = -1)
```

Change the value of the progress bar to `new_value`.

The color can be selected by the keyword `color`. It it is negative (**default**), then the current color will not be changed.
