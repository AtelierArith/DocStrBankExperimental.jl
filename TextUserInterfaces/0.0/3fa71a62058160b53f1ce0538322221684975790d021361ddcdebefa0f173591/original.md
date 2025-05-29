```
function move_view(win::Window, y::Integer, x::Integer; update::Bool = true)
```

Move the origin of the view of window `win` to the position `(y,x)`. This routine makes sure that the view will never reach positions outside the buffer.
