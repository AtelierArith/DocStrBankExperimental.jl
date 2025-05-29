```
UnivariateTimeTypeToContinuous
```

A model type for constructing a single variable transformer that creates continuous representations of temporally typed data, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
UnivariateTimeTypeToContinuous = @load UnivariateTimeTypeToContinuous pkg=MLJModels
```

Do `model = UnivariateTimeTypeToContinuous()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `UnivariateTimeTypeToContinuous(zero_time=...)`.

Use this model to convert vectors with a `TimeType` element type to vectors of `Float64` type (`Continuous` element scitype).

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, x)
```

where

  * `x`: any abstract vector whose element type is a subtype of `Dates.TimeType`

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `zero_time`: the time that is to correspond to 0.0 under transformations, with the type coinciding with the training data element type. If unspecified, the earliest time encountered in training is used.
  * `step::Period=Hour(24)`: time interval to correspond to one unit under transformation

# Operations

  * `transform(mach, xnew)`: apply the encoding inferred when `mach` was fit

# Fitted parameters

`fitted_params(mach).fitresult` is the tuple `(zero_time, step)` actually used in transformations, which may differ from the user-specified hyper-parameters.

# Example

```
using MLJ
using Dates

x = [Date(2001, 1, 1) + Day(i) for i in 0:4]

encoder = UnivariateTimeTypeToContinuous(zero_time=Date(2000, 1, 1),
                                         step=Week(1))

mach = machine(encoder, x)
fit!(mach)
julia> transform(mach, x)
5-element Vector{Float64}:
 52.285714285714285
 52.42857142857143
 52.57142857142857
 52.714285714285715
 52.857142
```
