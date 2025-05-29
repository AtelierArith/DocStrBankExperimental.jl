```
evaluate!(spline_grid::SplineGrid{Nin};
    derivative_order::NTuple{Nin, <:Integer} = ntuple(_ -> 0, Nin),
    control_points::AbstractArray = spline_grid.control_points,
    eval::AbstractArray = spline_grid.eval)
```

スプライングリッドを評価します。つまり、各スプライン次元の各サンプルポイントに対して評価された基底関数を取得し、基底関数の積を係数とした制御点の線形結合として各サンプルポイントの組み合わせで出力グリッドを計算します。

重みが供給される場合、制御点係数としてNURBSの有理基底関数を計算します。

デフォルトでは`spline_grid`から`control_points`および`eval`配列を使用しますが、最適化アルゴリズムの便宜のために異なる配列を指定することもできます。
