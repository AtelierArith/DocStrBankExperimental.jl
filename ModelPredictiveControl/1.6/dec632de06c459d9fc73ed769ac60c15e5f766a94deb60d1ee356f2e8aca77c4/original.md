```
default_nint(model::SimModel, i_ym=1:model.ny, nint_u=0)
```

One integrator on each measured output by default if `model` is not a  [`LinModel`](@ref).

Theres is no verification the augmented model remains observable. If the integrator quantity per manipulated input `nint_u ≠ 0`, the method returns zero integrator on each measured output.
