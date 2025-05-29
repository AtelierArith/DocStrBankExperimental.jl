```
bind_raw(f::Function, w::Webview, name::AbstractString)
```

Binds a callback so that it will appear in the webview with the given name as a global async JavaScript function. Callback receives a seq and req value. The seq parameter is an identifier for using `Webviews.return_raw` to return a value while the req parameter is a string of an JSON array representing the arguments passed from the JavaScript function call.

The callback function must has the method `f(seq::String, req::String)`.
