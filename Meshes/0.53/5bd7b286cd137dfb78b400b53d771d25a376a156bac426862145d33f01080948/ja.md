```
BezierCurve(points)
```

制御点 `points` を持つ再帰的なベジェ曲線。詳細は [https://en.wikipedia.org/wiki/Bézier_curve](https://en.wikipedia.org/wiki/Bézier_curve) を参照してください。曲線上の点 `b` は、`t` が `0` と `1` の間の値である `b(t)` を呼び出すことで評価できます。評価メソッドは、正確な評価のためにデカステリョーのアルゴリズムをデフォルトで使用します。多くの点でより速いが精度が低いホーナー法は、`b(t, Horner())` を介して使用できます。

## 例

```julia
BezierCurve([(0.,0.),(1.,-1.)])
```
