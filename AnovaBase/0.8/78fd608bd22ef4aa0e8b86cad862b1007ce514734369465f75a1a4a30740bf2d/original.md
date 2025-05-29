```
MixedAovModels{M, N} <: AnovaModel{M, N}
```

A wrapper of nested models of multiple types for conducting ANOVA.

  * `M` is a union type of regression models.
  * `N` is the number of models.

# Fields

  * `model`: a tuple of models.

# Constructors

```
MixedAovModels{M}(model...) where M 
MixedAovModels{M}(model::T) where {M, T <: Tuple}
```
