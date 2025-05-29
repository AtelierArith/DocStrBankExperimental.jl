```
UnivariateDiscretizer
```

A model type for constructing a single variable discretizer, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
UnivariateDiscretizer = @load UnivariateDiscretizer pkg=MLJModels
```

Do `model = UnivariateDiscretizer()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `UnivariateDiscretizer(n_classes=...)`.

Discretization converts a `Continuous` vector into an `OrderedFactor` vector. In particular, the output is a `CategoricalVector` (whose reference type is optimized).

The transformation is chosen so that the vector on which the transformer is fit has, in transformed form, an approximately uniform distribution of values. Specifically, if `n_classes` is the level of discretization, then `2*n_classes - 1` ordered quantiles are computed, the odd quantiles being used for transforming (discretization) and the even quantiles for inverse transforming.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, x)
```

where

  * `x`: any abstract vector with `Continuous` element scitype; check scitype with `scitype(x)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `n_classes`: number of discrete classes in the output

# Operations

  * `transform(mach, xnew)`: discretize `xnew` according to the discretization learned when fitting `mach`
  * `inverse_transform(mach, z)`: attempt to reconstruct from `z` a vector that transforms to give `z`

# Fitted parameters

The fields of `fitted_params(mach).fitesult` include:

  * `odd_quantiles`: quantiles used for transforming (length is `n_classes - 1`)
  * `even_quantiles`: quantiles used for inverse transforming (length is `n_classes`)

# Example

```
using MLJ
using Random
Random.seed!(123)

discretizer = UnivariateDiscretizer(n_classes=100)
mach = machine(discretizer, randn(1000))
fit!(mach)

julia> x = rand(5)
5-element Vector{Float64}:
 0.8585244609846809
 0.37541692370451396
 0.6767070590395461
 0.9208844241267105
 0.7064611415680901

julia> z = transform(mach, x)
5-element CategoricalArrays.CategoricalArray{UInt8,1,UInt8}:
 0x52
 0x42
 0x4d
 0x54
 0x4e

x_approx = inverse_transform(mach, z)
julia> x - x_approx
5-element Vector{Float64}:
 0.008224506144777322
 0.012731354778359405
 0.0056265330571125816
 0.005738175684445124
 0.006835652575801987
```
