```
etp = linear_interpolation(knots, A; extrapolation_bc=Throw())
```

次のいずれかの省略形です。

  * `extrapolate(scale(interpolate(A, BSpline(Linear())), knots), extrapolation_bc)`
  * `extrapolate(interpolate(knots, A, Gridded(Linear())), extrapolation_bc)`,

`knots` が範囲またはベクトルのいずれであるかに応じて。

この便利なコンストラクタを使用するのではなく、必要に応じて `interpolate`、`scale`、または `extrapolate` を明示的に使用することを検討してください。スケーリングや外挿なしでパフォーマンスが向上します。
