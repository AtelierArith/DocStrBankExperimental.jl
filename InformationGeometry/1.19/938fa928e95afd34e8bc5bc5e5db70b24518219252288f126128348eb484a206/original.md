```
DistanceMatrixWithinStep(DM::AbstractDataModel, R::MultistartResults, Ind::Int; logarithmic::Bool=true, plot::Bool=isloaded(:Plots), kwargs...)
```

Returns matrix of mutual distances between optima in step `Ind` with respect to Fisher Metric of first entry in step. 
