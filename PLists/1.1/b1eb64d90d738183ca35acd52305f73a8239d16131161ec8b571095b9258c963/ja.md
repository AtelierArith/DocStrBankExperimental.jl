```
addchildren!(parent, children::Vector{Pair{String, String}})
```

親ノード `p` に子要素を簡単に追加するための便利な関数です。

# 例

```
addchildren!(node, ["x" => "10", "y" => "20"])
```
