```
NestedModels{M, N} <: AnovaModel{M, N}
```

A wrapper of nested models of the same types for conducting ANOVA.

  * `M` is a type of regression model.
  * `N` is the number of models.

# Fields

  * `model`: a tuple of models.

# Constructors

```
NestedModels(model::Vararg{M, N}) where {M, N}
NestedModels(model::NTuple{N, M}) where {M, N}
```
