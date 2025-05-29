```
subspaceid(
    data::InputOutputData,
    nx = :auto;
    verbose = false,
    r = nx === :auto ? min(length(data) ÷ 20, 50) : nx + 10, # the maximal prediction horizon used
    s1 = r, # number of past outputs
    s2 = r, # number of past inputs
    W = :MOESP,
    zeroD = false,
    stable = true, 
    focus = :prediction,
    svd::F1 = svd!,
    scaleU = true,
    Aestimator::F2 = \,
    Bestimator::F3 = \,
    weights = nothing,
)
```

Estimate a state-space model using subspace-based identification. Several different subspace-based algorithms are available, and can be chosen using the `W` keyword. Options are `:MOESP, :CVA, :N4SID, :IVM`.

Ref: Ljung, Theory for the user.

Resistance against outliers can be improved by supplying a custom factorization algorithm and replacing the internal least-squares estimators. See the documentation for the keyword arguments `svd`, `Aestimator`, and `Bestimator` below.

The returned model is of type `N4SIDStateSpace` and contains the field `sys` with the system model, as well as covariance matrices for a Kalman filter.

# Arguments:

  * `data`: Identification data [`iddata`](@ref)
  * `nx`: Rank of the model (model order)
  * `verbose`: Print stuff?
  * `r`: Prediction horizon. The model may perform better on simulation if this is made longer, at the expense of more computation time.
  * `s1`: past horizon of outputs
  * `s2`: past horizon of inputs
  * `W`: Weight type, choose between `:MOESP, :CVA, :N4SID, :IVM`
  * `zeroD`: Force the `D` matrix to be zero.
  * `stable`: Stabilize unstable system using eigenvalue reflection.
  * `focus`: `:prediction` or `simulation`
  * `svd`: The function to use for `svd`. For resistance against outliers, consider using `TotalLeastSquares.rpca` to preprocess the data matrix before applying `svd`, like `svd = A->svd!(rpca(A)[1])`.
  * `scaleU`: Rescale the input channels to have the same energy.
  * `Aestimator`: Estimator function used to estimate `A,C`. The default is ``, i.e., least squares, but robust estimators, such as`irls, flts, rtls` from [TotalLeastSquares.jl](https://github.com/baggepinnen/TotalLeastSquares.jl/), can be used to gain resistance against outliers.
  * `Bestimator`: Estimator function used to estimate `B,D`. Weighted estimation can be eachieved by passing `wls` from TotalLeastSquares.jl together with the `weights` keyword argument.
  * `weights`: A vector of weights can be provided if the `Bestimator` is `wls`.

# Extended help

A more accurate prediciton model can sometimes be obtained using [`newpem`](@ref), which is also unbiased for closed-loop data (`subspaceid` is biased for closed-loop data, see example in the docs). The prediction-error method is iterative and generally more expensive than `subspaceid`, and uses this function (by default) to form the initial guess for the optimization.
