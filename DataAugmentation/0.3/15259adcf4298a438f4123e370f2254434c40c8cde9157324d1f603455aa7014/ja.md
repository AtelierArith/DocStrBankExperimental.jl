```
Image(image[, bounds]; interpolate=BSpline(Linear()), extrapolate=zero(T))
```

要素タイプ T の N 次元画像を表すアイテム。オプションで、補間および外挿方法を指定できます。ここでの補間は、変換されたコンテンツの境界に入る投影ピクセルの値がどのように計算されるかを指します。外挿は、投影されたコンテンツの境界の外にある値をどのように割り当てるかを指します。デフォルトは線形補間で、新しい領域をゼロで埋めることです。

!!! info
    `Interpolations` パッケージは、`interpolate` および `extrapolate` キーワード引数で使用するための多数の方法を提供します。たとえば、`BSpline(Linear())` と `BSpline(Constant())` は、それぞれ線形補間と最近傍補間を提供します。さらに、`Flat()`、`Reflect()`、および `Periodic()` 境界条件が外挿に利用可能です。


## 例

```julia
using DataAugmentation, Images

imagedata = rand(RGB, 100, 100)
item = Image(imagedata)
showitems(item)
```

もし `T` が色でない場合、画像はグレースケールとして解釈されます：

```julia
imagedata = rand(Float32, 100, 100)
item = Image(imagedata)
showitems(item)
```
