```julia
Q!(path::Component{:path}, a::Any ...) -> ::String
```

`Q!` adds a `Q` to the `d` data of a `path`.  The `Q` option  performs a quadratic bezier command. –-

```example
new_path = path("new-path")
M!(new_path, "100,250")
Q!(new_path, "250,100", "400,250")
Z!(new_path)
# -- display
display("text/html", window)
```
