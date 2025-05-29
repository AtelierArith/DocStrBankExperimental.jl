```
profileσ(m::LinearMixedModel, tc::TableColumns; threshold=4)
```

Return a Table of the profile of `σ` for model `m`.  The profile extends to where the magnitude of ζ exceeds `threshold`.

!!! note
    This method is called by `profile` and currently considered internal. As such, it may change or disappear in a future release without being considered breaking.

