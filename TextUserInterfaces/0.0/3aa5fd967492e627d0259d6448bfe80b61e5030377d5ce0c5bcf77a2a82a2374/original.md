```
function refresh_window(win::Window; update = true, backpropagation = true)
```

Refresh the window `win` and all its child windows. If the view needs to be updated (see `view_needs_update`), then the content of the buffer will be copied to the view before updating.

If `update` is `true`, then `doupdate()` is called and the physical screen is updated.

If `backpropagation` is `true`, then all the parents windows (except from the root window) will also be refreshed.
