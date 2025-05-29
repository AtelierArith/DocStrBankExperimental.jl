```
TotalLeastSquares(DM::DataModel, initialθ::AbstractVector=MLE(DM), start::AbstractVector=[xdata(DM);initialp]; tol::Real=1e-13, kwargs...) -> Vector
```

Experimental feature which takes into account uncertainties in x-values to improve the accuracy of the fit. Returns concatenated vector of x-values and parameters. Assumes that the uncertainties in the x-values and y-values are normal, i.e. Gaussian!
