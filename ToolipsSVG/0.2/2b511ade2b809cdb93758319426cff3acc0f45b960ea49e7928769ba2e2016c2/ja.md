```julia
M!(path::Component{:path}, points::Any ...) -> ::String
```

`M!` は `path` の `d` データに `M` を追加します。`M` は *move* であり、これは `path` カーソルを特定の位置に移動させます。 –-

```example
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

```example
cuteheart = path("heat")
M!(cuteheart, 12, "21.593c-5.63-5.539-11-10.297-11-14.402", 
"0-3.791 3.068-5.191 5.281-5.191 1.312", 0, "4.151.501", 
5.719, 4.457, "1.59-3.968", "4.464-4.447",
 "5.726-4.447", 2.54, 0, 5.274, 1.621, 5.274, 5.181, 0,
 "4.069-5.136 8.625-11", "14.402m5.726-20.583c-2.203", "0-4.446 1.042-5.726 3.238-1.285-2.206-3.522-3.248-5.719-3.248-3.183",
  "0-6.281", "2.187-6.281", 6.191, 0, 4.661, 5.571, 9.429, 12, 15.809, "6.43-6.38 12-11.148 12-15.809",
   "0-4.011-3.095-6.181-6.274-6.181")

window = svg("main", width = 500, height = 500)
push!(window, cuteheart)
display("text/html", window)
```
