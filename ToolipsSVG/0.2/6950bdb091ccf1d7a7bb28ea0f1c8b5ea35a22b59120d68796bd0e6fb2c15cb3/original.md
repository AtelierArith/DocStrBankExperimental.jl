```julia
L!(path::Component{:path}, points::Any ...) -> ::String
```

`L!` adds an `L` to the `d` data of a `path`. `L` is *line-to*, which draws  a line from the current path position to the new `xy` position. –-

```example
using ToolipsSVG
# create our path:
squarepath = path("new-square")
M!(squarepath, 50, 50)
L!(squarepath, 100, 50)
L!(squarepath, 100, 100)
L!(squarepath, 50, 100)
L!(squarepath, 50, 50)
Z!(squarepath)
# add to svg window:
window = svg("main", width = 500, height = 500)
push!(window, squarepath)
# -- display
display("text/html", window)
```
