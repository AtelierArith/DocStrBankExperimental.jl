```julia
Q!(path::Component{:path}, a::Any ...) -> ::String
```

`Q!` は `path` の `d` データに `Q` を追加します。 `Q` オプションは二次ベジェ曲線コマンドを実行します。 –-

```example
new_path = path("new-path")
M!(new_path, "100,250")
Q!(new_path, "250,100", "400,250")
Z!(new_path)
# -- display
display("text/html", window)
```
