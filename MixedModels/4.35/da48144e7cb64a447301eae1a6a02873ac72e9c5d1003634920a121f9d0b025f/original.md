```
issingular(bsamp::MixedModelFitCollection;
           atol::Real=0, rtol::Real=atol>0 ? 0 : √eps))
```

Test each bootstrap sample for singularity of the corresponding fit.

Equality comparisons are used b/c small non-negative θ values are replaced by 0 in `fit!`.

See also [`issingular(::MixedModel)`](@ref).
