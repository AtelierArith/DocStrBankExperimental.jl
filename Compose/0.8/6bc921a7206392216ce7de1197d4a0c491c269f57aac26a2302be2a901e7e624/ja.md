```
draw(b::Backend, c::Context)
```

与えられたバックエンドに `c` のツリー構造のグラフィックを出力します。

# 例

```
draw(SVGJS("foo.svg"), compose(context(), text(0,0,"foo")))
```
