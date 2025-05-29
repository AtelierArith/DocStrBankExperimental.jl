```
set_timeout(f::Function, w::Webview, interval::Real; [repeat::Bool=false])
```

Sets a function to be called after the given interval in webview's event loop. If `repeat` is `true`, `f` will be called repeatedly. The function `f` should be callable without arguments.

This function returns a `timer_id::Ptr{Cvoid}` which can be used in `clear_timeout(webview, timer_id)`.
