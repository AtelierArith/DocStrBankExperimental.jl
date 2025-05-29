```
function jlgetch(win::Union{Ptr{WINDOW},Nothing} = nothing)
```

Wait for an keystroke in the window `win` and return it (see `Keystroke`).  If `win` is `nothing`, then `getch()` will be used instead of `wgetch(win)` to listen for the keystroke.
