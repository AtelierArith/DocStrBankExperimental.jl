```
function change_text(widget::WidgetLabel, new_text::AbstractString; alignment = :l, color::Int = -1)
```

Change to text of the label widget `widget` to `new_text`.

The text alignment in the widget can be selected by the keyword `alignment`, which can be:

  * `:l`: left alignment (**default**);
  * `:c`: Center alignment; or
  * `:r`: Right alignment.

The text color can be selected by the keyword `color`. It it is negative (**default**), then the current color will not be changed.
