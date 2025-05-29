```
streamplot(f::function, xinterval, yinterval; color = norm, kwargs...)
```

fは`f(::Point)`または`f(x::Number, y::Number)`のいずれかを受け入れる必要があります。fはPoint2を返さなければなりません。

例:

```julia
v(x::Point2{T}) where T = Point2f(x[2], 4*x[1])
streamplot(v, -2..2, -2..2)
```

線の色は、`color`属性に関数`color_func(dx::Point)`を渡すことで選択できます。デフォルトでは`norm`に設定されていますが、任意の関数または関数の合成に設定できます。`color_func`に渡される`dx`は、色付けされる点での`f`の出力です。

## 属性

`MakieCore.Plot{Makie.streamplot}`の利用可能な属性とそのデフォルトは次のとおりです:

```
  alpha           1.0
  arrow_head      MakieCore.Automatic()
  arrow_size      MakieCore.Automatic()
  color           LinearAlgebra.norm
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  density         1.0
  depth_shift     0.0f0
  gridsize        (32, 32, 32)
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  maxsteps        500
  nan_color       :transparent
  overdraw        false
  quality         16
  space           :data
  ssao            false
  stepsize        0.01
  transparency    false
  visible         true
```

## 実装

実装の詳細については、`Makie.streamplot_impl`関数を参照してください。
