```
dispatch(f::Function, w::Webview)
```

Posts a function to be executed on the main thread. You normally do not need to call this function, unless you want to tweak the native window.

The function `f` should be callable without arguments.
