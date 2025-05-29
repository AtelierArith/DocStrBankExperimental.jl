```
evaluate_adjoint!(spline_grid::AbstractSplineGrid{Nin, Nout, false, Tv};
    derivative_order::NTuple{Nin, <:Integer} = ntuple(_ -> 0, Nin),
    control_points::AbstractControlPointArray{Nin, Nout, Tv} = spline_grid.control_points,
    eval::AbstractArray = spline_grid.eval)::Nothing where {Nin, Nout, Tv}
```

evaluate the adjoint of the linear mapping `control_points -> eval`. This is a computation of the form `eval -> control_points`. If we write `evaluate!(spline_grid)` as a matrix vector multiplication `eval = M * control_points`, Then the adjoint is given by `v -> M' * v`. This mapping is used in fitting algorithms.
