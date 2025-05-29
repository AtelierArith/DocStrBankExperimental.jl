```
LinearMixedModel(y, Xs, form, wts=[], σ=nothing, amalgamate=true)
```

Private constructor for a LinearMixedModel.

To construct a model, you only need the response (`y`), already assembled model matrices (`Xs`), schematized formula (`form`) and weights (`wts`). Everything else in the structure can be derived from these quantities.

!!! note
    This method is internal and experimental and so may change or disappear in a future release without being considered a breaking change.

