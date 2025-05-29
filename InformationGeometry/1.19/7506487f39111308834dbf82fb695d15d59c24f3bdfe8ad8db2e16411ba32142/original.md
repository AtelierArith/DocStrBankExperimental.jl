```
DataSetUncertain(x::AbstractVector, y::AbstractVector, σ⁻¹::Function, c::AbstractVector; BesselCorrection::Bool=false)
DataSetUncertain(x::AbstractVector, y::AbstractVector, σ⁻¹::Function, errorparamsplitter::Function, c::AbstractVector, dims::Tuple{Int,Int,Int}; BesselCorrection::Bool=false)
```

The `DataSetUncertain` type encodes data for which the size of the variance is unknown a-priori but whose error is specified via an error model of the form `σ(x, y_pred, c)` where `c` is a vector of error parameters. This parametrized error model is subsequently used to estimate the standard deviations in the observations `y`.

!!! note
    To enhance performance, the implementation actually requires the specification of a *reciprocal* error model, i.e. a function `σ⁻¹(x, y_pred, c)`. If `ydim` is larger than one, the reciprocal error model should output a matrix, i.e. the cholesky decomposition `S` of the covariance `Σ` such that `Σ == S' * S`.


To construct a `DataSetUncertain`, one has to specify a vector of independent variables `x`, a vector of dependent variables `y`, a reciprocal error model `σ⁻¹(x, y_pred, c)` and an initial guess for the vector of error parameters `c`. Optionally, an explicit `errorparamsplitter` function of the form `θ -> (modelparams, errorparams)` may be specified, which splits the parameters into a tuple of model parameters, which are subsequently forwarded into the model, and error parameters `c`, which are only passed to the reciprocal error model `σ⁻¹`.

!!! warn
    The parameters which are visible to the outside are processed by `errorparamsplitter` FIRST, before forwarding into the model, where `modelparams` might be further modified by embedding transformations.


# Examples:

In the simplest case, where all data points are mutually independent and have a single $x$-component and a single $y$-component each, a `DataSet` consisting of four points can be constructed via

```julia
DS = DataSetUncertain([1,2,3,4], [4,5,6.5,7.8], (x,y,c)->1/exp10(c[1]), [0.5])
```

!!! note
    It is generally advisable to exponentiate error parameters, since they are penalized poportional to `log(c)` in the normalization term of Gaussian likelihoods. A Bessel correction `sqrt((length(ydata(DS))-length(params))/length(ydata(DS)))` can be applied to the reciprocal error to account for the fact that the maximum likelihood estimator for the variance is biased via kwarg `BesselCorrection`.

