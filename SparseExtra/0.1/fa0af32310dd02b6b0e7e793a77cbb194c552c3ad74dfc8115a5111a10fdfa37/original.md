```
Path2Edge(x, [e=length(x)])
```

[Unbenchmarked] faster version of `zip(view(x, 1:e), view(x, 2:e))`. Only works on 1-index based arrays with unit strides
