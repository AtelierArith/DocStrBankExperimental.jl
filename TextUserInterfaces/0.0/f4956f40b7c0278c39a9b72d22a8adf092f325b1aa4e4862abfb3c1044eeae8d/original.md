```
function update(widget; force_redraw = false)
```

Update the widget by calling the function `redraw`. This function returns `true` if the widget needed to be updated of `false` otherwise.

If `force_redraw` is `true`, then the widget will be updated even if it is not needed.
