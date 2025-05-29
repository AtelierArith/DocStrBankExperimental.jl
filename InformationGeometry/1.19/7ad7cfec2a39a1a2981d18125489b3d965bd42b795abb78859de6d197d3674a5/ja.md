```
PracticallyIdentifiable(DM::AbstractDataModel, Confnum::Real=1; plot::Bool=isloaded(:Plots), IsCost::Bool=false, kwargs...) -> Real
```

与えられた `DataModel` が依然として実質的に同定可能である最大の信頼レベル（標準偏差 σ の単位で）を決定します。
