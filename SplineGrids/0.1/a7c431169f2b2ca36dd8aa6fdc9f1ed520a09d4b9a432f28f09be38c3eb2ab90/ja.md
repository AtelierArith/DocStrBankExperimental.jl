```
evaluate_adjoint!(spline_grid::AbstractSplineGrid{Nin, Nout, false, Tv};
    derivative_order::NTuple{Nin, <:Integer} = ntuple(_ -> 0, Nin),
    control_points::AbstractControlPointArray{Nin, Nout, Tv} = spline_grid.control_points,
    eval::AbstractArray = spline_grid.eval)::Nothing where {Nin, Nout, Tv}
```

線形写像 `control_points -> eval` の随伴を評価します。これは `eval -> control_points` の形の計算です。`evaluate!(spline_grid)` を行列ベクトルの乗算 `eval = M * control_points` と書くと、随伴は `v -> M' * v` で与えられます。この写像はフィッティングアルゴリズムで使用されます。
