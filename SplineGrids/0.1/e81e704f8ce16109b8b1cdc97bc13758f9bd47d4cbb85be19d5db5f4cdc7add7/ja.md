```
decompress(
    spline_dimension::SplineDimension{Tv}; derivative_order::Integer = 0) where {Tv}
```

`spline_dimension.eval`を形状`(n_sample_points, n_points - degree - 1)`の行列に変換し、各サンプルポイントでの各基底関数の値を明示的に示します。
