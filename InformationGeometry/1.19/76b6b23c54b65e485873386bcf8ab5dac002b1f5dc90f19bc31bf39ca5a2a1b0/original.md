```
IncrementalTimeSeriesFit(DM::AbstractDataModel, initial::AbstractVector{<:Number}=MLE(DM); steps::Int=length(Data(DM))÷5, Method::Function=InformationGeometry.minimize, kwargs...) -> Vector
```

Fits DataModel incrementally by splitting up the times series into chunks, e.g. fitting only the first quarter of data points, then half and so on. This can yield much better fitting results from random starting points, particularly for autocorrelated time series data. For example when the time series data oscillates in such a way that the optimization often gets stuck in a local optimum where the model fits a mostly straight line through the data, not correctly recognizing the oscillations.
