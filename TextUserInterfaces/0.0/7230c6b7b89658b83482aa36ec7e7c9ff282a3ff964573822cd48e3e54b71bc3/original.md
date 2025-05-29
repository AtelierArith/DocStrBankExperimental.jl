```
function update_view(win::Window; force::Bool = false)
```

Update the view of window `win` by copying the contents from the buffer. If the view does not need to be updated (see `view_needs_update`), then nothing is done. If the keyword `force` is `true`, then the copy will always happen.

# Return

It returns `true` if the view has been updated and `false` otherwise.
