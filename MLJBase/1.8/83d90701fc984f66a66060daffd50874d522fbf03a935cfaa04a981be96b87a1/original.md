```
machine(model, args...; cache=true, scitype_check_level=1)
```

Construct a `Machine` object binding a `model`, storing hyper-parameters of some machine learning algorithm, to some data, `args`. Calling [`fit!`](@ref) on a `Machine` instance `mach` stores outcomes of applying the algorithm in `mach`, which can be inspected using `fitted_params(mach)` (learned paramters) and `report(mach)` (other outcomes). This in turn enables generalization to new data using operations such as `predict` or `transform`:

```julia
using MLJModels
X, y = make_regression()

PCA = @load PCA pkg=MultivariateStats
model = PCA()
mach = machine(model, X)
fit!(mach, rows=1:50)
transform(mach, selectrows(X, 51:100)) # or transform(mach, rows=51:100)

DecisionTreeRegressor = @load DecisionTreeRegressor pkg=DecisionTree
model = DecisionTreeRegressor()
mach = machine(model, X, y)
fit!(mach, rows=1:50)
predict(mach, selectrows(X, 51:100)) # or predict(mach, rows=51:100)
```

Specify `cache=false` to prioritize memory management over speed.

When building a learning network, `Node` objects can be substituted for the concrete data but no type or dimension checks are applied.

### Checks on the types of training data

A model articulates its data requirements using [scientific types](https://juliaai.github.io/ScientificTypes.jl/dev/), i.e., using the [`scitype`](@ref) function instead of the `typeof` function.

If `scitype_check_level > 0` then the scitype of each `arg` in `args` is computed, and this is compared with the scitypes expected by the model, unless `args` contains `Unknown` scitypes and `scitype_check_level < 4`, in which case no further action is taken. Whether warnings are issued or errors thrown depends the level. For details, see [`default_scitype_check_level`](@ref), a method to inspect or change the default level (`1` at startup).

### Machines with model placeholders

A symbol can be substituted for a model in machine constructors to act as a placeholder for a model specified at training time. The symbol must be the field name for a struct whose corresponding value is a model, as shown in the following example:

```julia
mutable struct MyComposite
    transformer
    classifier
end

my_composite = MyComposite(Standardizer(), ConstantClassifier)

X, y = make_blobs()
mach = machine(:classifier, X, y)
fit!(mach, composite=my_composite)
```

The last two lines are equivalent to

```julia
mach = machine(ConstantClassifier(), X, y)
fit!(mach)
```

Delaying model specification is used when exporting learning networks as new stand-alone model types. See [`prefit`](@ref) and the MLJ documentation on learning networks.

See also [`fit!`](@ref), [`default_scitype_check_level`](@ref), [`MLJBase.save`](@ref), [`serializable`](@ref).
