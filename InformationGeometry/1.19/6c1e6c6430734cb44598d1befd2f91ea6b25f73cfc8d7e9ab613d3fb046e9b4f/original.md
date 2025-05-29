```
PracticallyIdentifiable(P::ParameterProfiles) -> Real
```

Determines the maximum level at which ALL the given profiles in `ParameterProfiles` are still practically identifiable. If `IsCost=true` was chosen for the profiles, the output is the maximal deviation in cost function value `2(L_MLE - PL_i(θ))`. If instead `IsCost=false` was chosen, so that cost function deviations have already been rescaled to confidence levels, the output of `PracticallyIdentifiable` is the maximal confidence level in units of standard deviations σ where the model is still practically identifiability.
