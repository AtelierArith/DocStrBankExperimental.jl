```
CatmullRomSpline([T=Float64,] B=Flat)
```

は、浮動小数点型 `T` と境界条件 `B` のための Catmull-Rom 補間カーネルのインスタンスを生成します。

Catmull-Rom 補間カーネルは、次のように定義される区分的な基準三次スプラインです：

```
ker(x) = ((3/2)*|x| - (5/2))*x^2 + 1             もし |x| ≤ 1 の場合
         (((5/2) - (1/2)*|x|)*|x| - 4)*|x| + 2   もし 1 ≤ |x| ≤ 2 の場合
         0                                       もし |x| ≥ 2 の場合
```

Catmull-Rom カーネルは、Mitchell & Netravali カーネルの特別なケースです（[`MitchellNetravaliSplinePrime`](@ref) を参照）。

式 `ker'` は、Catmull-Rom 補間カーネル `ker` の 1 次導関数であるカーネルインスタンスを生成します（[`CatmullRomSplinePrime`](@ref) のコンストラクタも参照）。
