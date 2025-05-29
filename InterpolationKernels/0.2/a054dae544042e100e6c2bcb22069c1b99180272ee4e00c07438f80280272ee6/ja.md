```
CubicSpline{T}(a, b) -> ker
```

は、浮動小数点型 `T` とパラメータ `a = ker'(1)` および `b = ker(1)` の一般的な三次スプラインのインスタンスを生成します。ここで、スロープは `ker(x)` の値であり、`x = 1` のときの値です。

三次スプラインカーネルは少なくとも C¹ 連続であり、式 `ker'` は一般的な三次スプライン `ker` の 1 次導関数を実装するカーネルインスタンスを生成します（導関数を直接構築するには [`CubicSplinePrime`](@ref) を参照してください）。

パラメータ `a` と `b` の値に応じて、より特定の三次スプラインカーネルをエミュレートできます：

  * `CubicSpline{T}(-1/2,1/6)` は、`BSpline{4,T}()` によって構築された三次 B スプラインを生成します。
  * `CubicSpline{T}(a,0)` は、`CardinalCubicSpline{T}(a)` によって構築された基準三次スプラインを生成します。
  * `CubicSpline{T}(-1/2,0)` は、`CatmullRomSpline{T}()` によって構築された Catmull-Rom カーネルを生成します。
  * `CubicSpline{T}(-b/2-c,b/6)` は、`MitchellNetravaliSpline{T}(b,c)` によって構築された Mitchell & Netravali 三次スプラインを生成します。

`CubicSpline` のインスタンスは非常に最適化されており、実際にはこれらのより専門的な対応物と同じくらい速いか、さらにはそれ以上に速い場合があります。
