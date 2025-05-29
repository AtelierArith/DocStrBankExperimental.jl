```
etp = cubic_spline_interpolation(knots, A; bc=Line(OnGrid()), extrapolation_bc=Throw())
```

`extrapolate(scale(interpolate(A, BSpline(Cubic(bc))), knots), extrapolation_bc)` の省略形です。

この便利なコンストラクタを使用するのではなく、必要に応じて `interpolate`、`scale`、または `extrapolate` を明示的に使用することを検討してください。スケーリングや外挿を行わないことで、パフォーマンスが向上します。
