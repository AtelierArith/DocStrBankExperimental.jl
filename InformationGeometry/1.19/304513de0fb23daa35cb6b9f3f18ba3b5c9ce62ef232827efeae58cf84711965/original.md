In addition to storing a `DataSet`, a `DataModel` also contains a function `model(x,θ)` and its derivative `dmodel(x,θ)` where `x` denotes the x-value of the data and `θ` is a vector of parameters on which the model depends. Crucially, `dmodel` contains the derivatives of the model with respect to the parameters `θ`, not the x-values. For example

```julia
DS = DataSet([1,2,3,4], [4,5,6.5,7.8], [0.5,0.45,0.6,0.8])
model(x::Number, θ::AbstractVector{<:Number}) = θ[1] * x + θ[2]
DM = DataModel(DS, model)
```

In cases where the output of the model has more than one component (i.e. `ydim > 1`), it is advisable to define the model function in such a way that it outputs static vectors using **StaticArrays.jl** for increased performance. For `ydim = 1`, **InformationGeometry.jl** expects the model to output a number instead of a vector with one component. In contrast, the parameter configuration `θ` must always be supplied as a vector (even if it only has a single component).

An initial guess for the maximum likelihood parameters can optionally be passed to the `DataModel` as a vector via

```julia
DM = DataModel(DS, model, [1.0,2.5])
```

During the construction of a `DataModel` process which includes the search for the maximum likelihood estimate $\theta_\text{MLE}$, multiple tests are run. If necessary, the maximum likelihood estimation and subsequent tests are both skipped by appending `true` as the last argument in the constructor or by using the respective kwargs `SkipTests=false` or `SkipOptim=false`:

```julia
DM = DataModel(DS, model, [-Inf,π,1], true)
```

If a `DataModel` is constructed as shown in the above examples, the gradient of the model with respect to the parameters `θ` (i.e. its "Jacobian") will be calculated using automatic differentiation. Alternatively, an explicit analytic expression for the Jacobian can be specified by hand:

```julia
using StaticArrays
function dmodel(x::Number, θ::AbstractVector{<:Number})
   @SMatrix [x  1.]     # ∂(model)/∂θ₁ and ∂(model)/∂θ₂
end
DM = DataModel(DS, model, dmodel)
```

The output of the Jacobian must be a matrix whose columns correspond to the partial derivatives with respect to different components of `θ` and whose rows correspond to evaluations at different components of `x`. Again, although it is not strictly required, outputting the Jacobian in form of a static matrix is typically beneficial for the overall performance.

It is also possible to specify a (logarithmized) prior distribution on the parameter space to the `DataModel` constructor after the initial guess for the MLE. For example:

```julia
using Distributions
Dist = MvNormal(ones(2), [1 0; 0 3.])
LogPriorFn(θ) = logpdf(Dist, θ)
DM = DataModel(DS, model, [1.0,2.5], LogPriorFn)
```

The `DataSet` contained in a `DataModel` named `DM` can be accessed via `Data(DM)`, whereas the model and its Jacobian can be used via `Predictor(DM)` and `dPredictor(DM)` respectively. The MLE and the value of the log-likelihood at the MLE are accessible via `MLE(DM)` and `LogLikeMLE(DM)`. The logarithmized prior can be accessed via `LogPrior(DM)`.
