```
SelfOrganizingMap
```

A model type for constructing a self organizing map, based on [SelfOrganizingMaps.jl](https://github.com/john-waczak/SelfOrganizingMaps.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
SelfOrganizingMap = @load SelfOrganizingMap pkg=SelfOrganizingMaps
```

Do `model = SelfOrganizingMap()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `SelfOrganizingMap(k=...)`.

SelfOrganizingMaps implements [Kohonen's Self Organizing Map](https://ieeexplore.ieee.org/abstract/document/58325?casa_token=pGue0TD38nAAAAAA:kWFkvMJQKgYOTJjJx-_bRx8n_tnWEpau2QeoJ1gJt0IsywAuvkXYc0o5ezdc2mXfCzoEZUQXSQ), Proceedings of the IEEE; Kohonen, T.; (1990):"The self-organizing map"

# Training data

In MLJ or MLJBase, bind an instance `model` to data with     mach = machine(model, X) where

  * `X`: an `AbstractMatrix` or `Table` of input features whose columns are of scitype `Continuous.`

Train the machine with `fit!(mach, rows=...)`.

# Hyper-parameters

  * `k=10`: Number of nodes along once side of SOM grid. There are `k²` total nodes.
  * `η=0.5`: Learning rate. Scales adjust made to winning node and its neighbors during each round of training.
  * `σ²=0.05`: The (squared) neighbor radius. Used to determine scale for neighbor node adjustments.
  * `grid_type=:rectangular`  Node grid geometry. One of `(:rectangular, :hexagonal, :spherical)`.
  * `η_decay=:exponential` Learning rate schedule function. One of `(:exponential, :asymptotic)`
  * `σ_decay=:exponential` Neighbor radius schedule function. One of `(:exponential, :asymptotic, :none)`
  * `neighbor_function=:gaussian` Kernel function used to make adjustment to neighbor weights. Scale is set by `σ²`. One of `(:gaussian, :mexican_hat)`.
  * `matching_distance=euclidean` Distance function from `Distances.jl` used to determine winning node.
  * `Nepochs=1` Number of times to repeat training on the shuffled dataset.

# Operations

  * `transform(mach, Xnew)`: returns the coordinates of the winning SOM node for each instance of `Xnew`. For SOM of grid*type `:rectangular` and `:hexagonal`, these are cartesian coordinates. For grid*type `:spherical`, these are the latitude and longitude in radians.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `coords`: The coordinates of each of the SOM nodes (points in the domain of the map) with shape (k², 2)
  * `weights`: Array of weight vectors for the SOM nodes (corresponding points in the map's range) of shape (k², input dimension)

# Report

The fields of `report(mach)` are:

  * `classes`: the index of the winning node for each instance of the training data X interpreted as a class label

# Examples

```
using MLJ
som = @load SelfOrganizingMap pkg=SelfOrganizingMaps
model = som()
X, y = make_regression(50, 3) # synthetic data
mach = machine(model, X) |> fit!
X̃ = transform(mach, X)

rpt = report(mach)
classes = rpt.classes
```
