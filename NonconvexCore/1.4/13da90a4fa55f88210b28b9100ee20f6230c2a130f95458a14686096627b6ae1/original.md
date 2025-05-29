```
optimize(
    model::AbstractModel,
    optimizer::AbstractOptimizer = MMA02(),
    x0::AbstractVector;
    options,
    convcriteria::ConvergenceCriteria = KKTCriteria(),
    plot_trace::Bool = false,
    callback::Function = plot_trace ? LazyPlottingCallback() : NoCallback(),
    kwargs...,
)

```

Optimizes `model` using the algorithm `optimizer`, e.g. an instance of [`MMA87`](@ref) or [`MMA02`](@ref). `x0` is the initial solution. The keyword arguments are:

  * `options`: used to set the optimization options. It is an instance of [`MMAOptions`](@ref) for [`MMA87`](@ref) and [`MMA02`](@ref).
  * `convcriteria`: an instance of [`ConvergenceCriteria`](@ref) that specifies the convergence criteria of the MMA algorithm.
  * `plot_trace`: a Boolean that if true specifies the callback to be an instance of [`PlottingCallback`](@ref) and plots a live trace of the last 50 solutions.
  * `callback`: a function that is called on `solution` in every iteration of the algorithm. This can be used to store information about the optimization process.

The details of the MMA optimization algorithms can be found in the original [1987 MMA paper](https://onlinelibrary.wiley.com/doi/abs/10.1002/nme.1620240207) and the [2002 paper](https://epubs.siam.org/doi/abs/10.1137/S1052623499362822).
