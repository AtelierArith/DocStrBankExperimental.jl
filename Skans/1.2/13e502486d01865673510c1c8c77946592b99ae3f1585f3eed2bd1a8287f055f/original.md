```
WebPage(url::AbstractString; selector::Function=clean) <: Page
```

WebPage to be scanned with `url`. The `selector` is a function which can be used to scan only a specific region of the page for changes. By default, only the `body` is taken into account. To take the full page, pass `selector=identity`.
