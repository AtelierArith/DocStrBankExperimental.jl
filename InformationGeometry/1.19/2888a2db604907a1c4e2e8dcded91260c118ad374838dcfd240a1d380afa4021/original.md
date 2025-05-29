```
PlotMatrix(Mat::AbstractMatrix, mle::AbstractVector; Confnum::Real=0., dims::Tuple{Int,Int}=(1,2), N::Int=400, plot::Bool=isloaded(:Plots), OverWrite::Bool=true, kwargs...)
```

Plots ellipse corresponding to a given covariance matrix which may additionally be offset by a vector `mle`. By providing information on the confidence level of the given matrix via the `Confnum` kwarg, a correction factor is computed to rescale the given matrix appropriately.

Example:

```
PlotMatrix(inv(FisherMetric(DM,mle)),mle)
```
