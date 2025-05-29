```
arrows(points, directions; kwargs...)
arrows(x, y, u, v)
arrows(x::AbstractVector, y::AbstractVector, u::AbstractMatrix, v::AbstractMatrix)
arrows(x, y, z, u, v, w)
```

指定された点に指定された成分で矢印をプロットします。`u` と `v` はベクトル成分として解釈され（`u` が x で `v` が y）、ベクトルは `x`、`y` に尾を持ってプロットされます。

もし `x, y, u, v` が `<: AbstractVector` の場合、各「行」は単一のベクトルとしてプロットされます。

もし `u, v` が `<: AbstractMatrix` の場合、`x` と `y` はグリッドの仕様として解釈され、`u, v` はグリッドに沿って矢印としてプロットされます。

`arrows` は三次元でも動作します。

## 属性

`AbstractPlotting.Combined{AbstractPlotting.arrows!}` の利用可能な属性とそのデフォルトは次のとおりです: 

```

```
