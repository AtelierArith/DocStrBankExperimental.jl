```julia
L!(path::Component{:path}, points::Any ...) -> ::String
```

`L!`は`path`の`d`データに`L`を追加します。`L`は*line-to*で、現在のパス位置から新しい`xy`位置までの線を描画します。 –-

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
# svgウィンドウに追加します:
window = svg("main", width = 500, height = 500)
push!(window, squarepath)
# -- 表示
display("text/html", window)
```
