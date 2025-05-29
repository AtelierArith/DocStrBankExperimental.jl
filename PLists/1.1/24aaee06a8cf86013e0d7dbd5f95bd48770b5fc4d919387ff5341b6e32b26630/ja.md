```
addchildren!(parent, children::Vector{Node})
```

親ノードに複数の子ノードを簡単に追加するためのものです。

# 例

```
addchildren!(node, [ElementNode("foo"), ElementNode("bar")])
```
