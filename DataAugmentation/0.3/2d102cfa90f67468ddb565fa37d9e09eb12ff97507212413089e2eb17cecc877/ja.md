```
MaskMulti(a, [classes]; interpolate=BSpline(Constant()), extrapolate=Flat())
```

`classes`のラベルを持つ`N`次元のマルチラベルマスク。オプションで、補間および外挿の方法を指定できます。ここでの補間は、変換されたコンテンツの境界に入る投影ピクセルの値がどのように計算されるかを指します。外挿は、投影されたコンテンツの境界の外にある値をどのように割り当てるかを指します。デフォルトは最近傍補間と新しい領域への平坦外挿です。

!!! info
    `Interpolations`パッケージは、`interpolate`および`extrapolate`キーワード引数で使用するための多数の方法を提供します。たとえば、`BSpline(Linear())`および`BSpline(Constant())`は、それぞれ線形補間と最近傍補間を提供します。さらに、外挿のために`Flat()`、`Reflect()`、および`Periodic()`境界条件が利用可能です。


## 例

```julia
using DataAugmentation

mask = MaskMulti(rand(1:3, 100, 100))
```

```julia
showitems(mask)
```
