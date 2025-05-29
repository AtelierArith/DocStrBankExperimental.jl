```
function sync_cursor(window::Window)
```

Synchronize the cursor to the position of the focused widget in window `window`. This is necessary because all the operations are done in the buffer and then copied to the view.
