```
Webview(
    size=(1024, 768);
    title="",
    debug=false,
    size_fixed=false,
    unsafe_window_handle=C_NULL,
    enable_webio=true,
    auto_terminate=true
)
Webview(width, height; kwargs...)
```

Create a new webview instance with `size` and `title`.

  * If `debug` is true, developer tools will be enabled (if the platform supports them).
  * **UNSAFE** `unsafe_window_handle` can be an unsafe pointer to the platforms specific native window handle.

If it's non-null - then child WebView is embedded into the given parent window. Otherwise a new window is created. Depending on the platform, a `GtkWindow`, `NSWindow` or `HWND` pointer can be passed here.

  * If `enable_webio` is true, then WebIO will be enabled.
  * The process will be terminated when all webviews with `auto_terminate=true` are destroyed.
