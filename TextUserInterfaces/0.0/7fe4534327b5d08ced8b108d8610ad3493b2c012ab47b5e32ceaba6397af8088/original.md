```
function create_widget(T, parent::Window, begin_y::Integer, begin_x::Integer, vargs...; kwargs...)
```

Create the widget of type `T` in the parent window `parent`. The widget will be positioned on the coordinate `(begin_y, begin_x)` of the parent window.

Additional variables and keywords related to each widget can be passed using `vargs` and `kwargs` respectively.
