```
feature_importances(model::M, fitresult, report)
```

For a given `model` of model type `M` supporting intrinsic feature importances, calculate the feature importances from the model's `fitresult` and `report` as an abstract vector of `feature::Symbol => importance::Real` pairs (e.g `[:gender =>0.23, :height =>0.7, :weight => 0.1]`).

# New model implementations

The following trait overload is also required: `MLJModelInterface.reports_feature_importances(::Type{<:M}) = true`

If for some reason a model is sometimes unable to report feature importances then `feature_importances` should return all importances as 0.0, as in `[:gender =>0.0, :height =>0.0, :weight => 0.0]`.
