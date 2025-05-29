```
contour([x,] [y,] z::Matrix, labels = true, [axes,] args...) -> Gaston.Figure
```

サーフェス `z` によって与えられる等高線をプロットします。`labels = false` の場合、プロットにはラベルが含まれません。

```
contour(x, y, f::Function, args...) -> Gaston.Figure
```

サーフェス `f.(x,y)` の等高線をプロットします。
