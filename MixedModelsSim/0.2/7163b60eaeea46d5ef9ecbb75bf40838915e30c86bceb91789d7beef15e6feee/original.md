```
update!(m::MixedModel, re...)
```

Update the mixed model to use the random-effects covariance matrices.

The `re` can be created using [`create_re`](@ref).

They should be specified in the order specified in `VarCorr(m)`.

!!! warning
    We recommend against calling this method directly. Instead, use the method with keyword arguments to specify the  different `re` by name.


!!! note
    This is a convenience function for installing a particular parameter vector and the resulting model fit. It does not actually perform any type of optimization.


# Details

The `re` used as the λ fields of the model's `ReTerm`s and should be specified as the lower Cholesky factor of covariance matrices.
