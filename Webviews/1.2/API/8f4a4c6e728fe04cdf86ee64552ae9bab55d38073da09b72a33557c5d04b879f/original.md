```
html!(w::Webview, html::AbstractString)
html!(w::Webview, body)
```

Set webview HTML directly. If `body` is not a string, such as a `WebIO.Node`, it will be converted to HTML first.
