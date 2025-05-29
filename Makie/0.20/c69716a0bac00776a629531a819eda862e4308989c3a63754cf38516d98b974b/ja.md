```
arrows(points, directions; kwargs...)
arrows(x, y, u, v)
arrows(x::AbstractVector, y::AbstractVector, u::AbstractMatrix, v::AbstractMatrix)
arrows(x, y, z, u, v, w)
arrows(x, y, [z], f::Function)
```

指定された点に指定された成分で矢印をプロットします。`u` と `v` はベクトル成分として解釈され（`u` が x で `v` が y）、ベクトルは `x`、`y` で尾を持つようにプロットされます。

`x, y, u, v` が `<: AbstractVector` の場合、各「行」は単一のベクトルとしてプロットされます。

`u, v` が `<: AbstractMatrix` の場合、`x` と `y` はグリッドの仕様として解釈され、`u, v` はグリッドに沿って矢印としてプロットされます。

`arrows` は三次元でも動作します。

`u, v, [w]` の代わりに `Function` が提供される場合、それは `Point` を入力として受け取り、適切な次元の `Point`、`Vec`、または他の配列のような出力を返す必要があります。

## 属性

`MakieCore.Arrows` の利用可能な属性とそのデフォルトは次のとおりです：

```
  align           :origin
  alpha           1.0
  arrowcolor      MakieCore.Automatic()
  arrowhead       MakieCore.Automatic()
  arrowsize       MakieCore.Automatic()
  arrowtail       MakieCore.Automatic()
  backlight       0.0f0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  depth_shift     0.0f0
  diffuse         1.0
  highclip        MakieCore.Automatic()
  inspectable     true
  lengthscale     1.0f0
  linecolor       MakieCore.Automatic()
  linestyle       "nothing"
  linewidth       MakieCore.Automatic()
  lowclip         MakieCore.Automatic()
  markerspace     :pixel
  nan_color       :transparent
  normalize       false
  overdraw        false
  quality         32
  shading         MakieCore.Automatic()
  shininess       32.0f0
  space           :data
  specular        0.2
  ssao            false
  transparency    false
  visible         true
```
