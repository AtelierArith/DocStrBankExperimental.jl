```
window_handle(w::Webview)
```

**UNSAFE** An unsafe pointer to the webviews platform specific native window handle. When using GTK backend the pointer is `GtkWindow` pointer, when using Cocoa backend the pointer is `NSWindow` pointer, when using Win32 backend the pointer is `HWND` pointer.
