```
surf([x,] [y,] z, [axes,] args...)-> Gaston.Figure
```

指定された `z` によって表される表面をプロットします。軸の仕様は `axes` です。

```
surf(x, y f::Function, args...)-> Gaston.Figure
```

表面 `f.(x,y)` をプロットします。
