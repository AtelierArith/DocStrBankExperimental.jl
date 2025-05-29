spy(x::Range, y::Range, z::AbstractSparseArray)

大きなスパース行列を視覚化します。使用法：

```julia
N = 200_000
x = sprand(Float64, N, N, (3(10^6)) / (N*N));
spy(x)
# または、xとyの範囲を指定したい場合：
spy(0..1, 0..1, x)
```

## 属性

`AbstractPlotting.Spy`の利用可能な属性とそのデフォルトは次のとおりです：

```
  colormap     :viridis
  colorrange   AbstractPlotting.Automatic()
  framecolor   :black
  framesize    1
  inspectable  true
  marker       AbstractPlotting.Automatic()
  markersize   AbstractPlotting.Automatic()
```
