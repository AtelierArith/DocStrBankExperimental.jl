```
update!(m::MixedModel; namedre...)
update!(m::MixedModel; θ)
```

Update the mixed model to use the random-effects covariance matrices.

The `namedre` can be created using [`create_re`](@ref). The `namedre` are specified by the name of the blocking variable, e.g. `subj=create_re(...)`.

!!! warning
    The model's response must be initialized to a non-constant value before calling this function, otherwise the model update will fail with a  `PosDefException`.


!!! warning
    Setting θ directly as a keyword-argument is deprecated.


!!! note
    This is a convenience function for installing a particular parameter vector and the resulting model fit. It does not actually perform any type of optimization.


# Details

The `re` is used as the λ fields of the model's `ReTerm`s and should be specified as the lower Cholesky factor of covariance matrices.
