```julia
Z!(path::Component{:path}) -> ::String
```

## `Z!` は `path` の `d` データに `Z` を追加します。`Z` は `path` を閉じるために使用されます。

```example
using ToolipsSVG
# パスを作成します:
squarepath = path("new-square")
M!(squarepath, 50, 50)
L!(squarepath, 100, 50)
L!(squarepath, 100, 100)
L!(squarepath, 50, 100)
L!(squarepath, 50, 50)
Z!(squarepath)
# svg ウィンドウに追加します:
window = svg("main", width = 500, height = 500)
push!(window, squarepath)
# -- 表示
display("text/html", window)
```
