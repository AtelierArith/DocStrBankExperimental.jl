```
SplineGrid(spline_dimensions::NTuple{Nin, <:SplineDimension{Tv, Ti}}, Nout::Integer)::SplineGrid{Nin, Tv, Ti} where {Nin, Tv, Ti}
```

NTupleのスプライン次元と出力次元の数から`SplineGrid`を定義します。

## 入力

  * `spline_dimensions`: スプライン次元のNTuple
  * `Nout`: 出力次元の数。すなわち、制御点はℝ^Noutに存在し、したがってスプラインもそこに存在します。
