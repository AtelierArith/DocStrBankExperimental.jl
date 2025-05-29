```
PracticallyIdentifiable(DM::AbstractDataModel, Confnum::Real=1; plot::Bool=isloaded(:Plots), IsCost::Bool=false, kwargs...) -> Real
```

Determines the maximum confidence level (in units of standard deviations σ) at which the given `DataModel` is still practically identifiable.
