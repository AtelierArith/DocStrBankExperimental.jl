```
ApproxConfidenceBands(DM::AbstractDataModel, ParameterCube::HyperCube, Xdomain=XCube(DM); N::Int=300, plot::Bool=isloaded(:Plots))
```

Computes confidence bands associated with the face centers of the `ParameterCube`. If the `ParameterCube` circumscribes a given confidence region, this will typically result in a gross and asymmetric overestimation of the true pointwise confidence bands associated with this confidence level.
