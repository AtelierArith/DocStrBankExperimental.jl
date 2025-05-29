```
etp = constant_interpolation(knots, A; extrapolation_bc=Throw())
```

`extrapolate(interpolate(knots, A, scheme), extrapolation_bc)`の省略形であり、ここで`scheme`は`knots`が範囲かベクトルかに応じて`BSpline(Constant())`または`Gridded(Constant())`のいずれかです。

この便利なコンストラクタを使用するのではなく、必要に応じて`interpolate`または`extrapolate`を明示的に使用することを検討してください。外挿なしでパフォーマンスが向上します。
