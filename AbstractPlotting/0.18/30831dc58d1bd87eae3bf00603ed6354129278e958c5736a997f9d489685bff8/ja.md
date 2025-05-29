streamplot(f::function, xinterval, yinterval; kwargs...)

fは`f(::Point)`または`f(x::Number, y::Number)`のいずれかを受け入れる必要があります。fはPoint2を返さなければなりません。

例:

```julia
v(x::Point2{T}) where T = Point2f0(x[2], 4*x[1])
streamplot(v, -2..2, -2..2)
```

## 属性

`AbstractPlotting.Combined{AbstractPlotting.streamplot!}`の利用可能な属性とそのデフォルトは次のとおりです:

```

```

## 実装

実装の詳細については、`AbstractPlotting.streamplot_impl`関数を参照してください。
