```
init(w::Webview, js::AbstractString)
```

Injects JavaScript code at the initialization of the new page. Every time the webview will open a the new page - this initialization code will be executed. It is guaranteed that code is executed before `window.onload`.
