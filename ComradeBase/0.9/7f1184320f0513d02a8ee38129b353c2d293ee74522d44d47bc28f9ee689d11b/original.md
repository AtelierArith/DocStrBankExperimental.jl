```
visibility(mimg, p)
```

Computes the complex visibility of model `m` at coordinates `p`. `p` corresponds to the coordinates of the model. These need to have the properties `U`, `V` and sometimes `Ti` for time and `Fr` for frequency.

# Notes

If you want to compute the visibilities at a large number of positions consider using the [`visibilitymap`](@ref visibilitymap).

# Warn

This is only defined for analytic models. If you want to compute the visibility for a single point for a non-analytic model, please use the `visibilitymap` function and create an `UnstructuredDomain` with a single point.
