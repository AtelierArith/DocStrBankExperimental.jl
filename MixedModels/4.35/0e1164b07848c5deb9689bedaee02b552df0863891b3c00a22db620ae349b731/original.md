```
LinearMixedModel(y, feterm, reterms, form, wts=[], σ=nothing; amalgamate=true)
```

Private constructor for a `LinearMixedModel` given already assembled fixed and random effects.

To construct a model, you only need a vector of `FeMat`s (the fixed-effects model matrix and response), a vector of `AbstractReMat` (the random-effects model matrices), the formula and the weights. Everything else in the structure can be derived from these quantities.

!!! note
    This method is internal and experimental and so may change or disappear in a future release without being considered a breaking change.

