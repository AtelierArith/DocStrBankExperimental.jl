```
Grid(goal=nothing, resolution=10, rng=Random.GLOBAL_RNG, shuffle=true)
```

Instantiate a Cartesian grid-based hyperparameter tuning strategy with a specified number of grid points as `goal`, or using a specified default `resolution` in each numeric dimension.

### Supported ranges:

A single one-dimensional range or vector of one-dimensioinal ranges can be specified. Specifically, in `Grid` search, the `range` field of a `TunedModel` instance can be:

  * A single one-dimensional range - ie, `ParamRange` object - `r`, or pair of the form `(r, res)` where `res` specifies a resolution to override the default `resolution`.
  * Any vector of objects of the above form

Two elements of a `range` vector may share the same `field` attribute, with the effect that their grids are combined, as in Example 3 below.

`ParamRange` objects are constructed using the `range` method.

Example 1:

```
range(model, :hyper1, lower=1, origin=2, unit=1)
```

Example 2:

```
[(range(model, :hyper1, lower=1, upper=10), 15),
  range(model, :hyper2, lower=2, upper=4),
  range(model, :hyper3, values=[:ball, :tree])]
```

Example 3:

```
# a range generating the grid `[1, 2, 10, 20, 30]` for `:hyper1`:
[range(model, :hyper1, values=[1, 2]),
 (range(model, :hyper1, lower= 10, upper=30), 3)]
```

Note: All the `field` values of the `ParamRange` objects (`:hyper1`, `:hyper2`, `:hyper3` in the preceding example) must refer to field names a of single model (the `model` specified during `TunedModel` construction).

### Algorithm

This is a standard grid search with the following specifics: In all cases all `values` of each specified `NominalRange` are exhausted. If `goal` is specified, then all resolutions are ignored, and a global resolution is applied to the `NumericRange` objects that maximizes the number of grid points, subject to the restriction that this not exceed `goal`. (This assumes no field appears twice in the `range` vector.) Otherwise the default `resolution` and any parameter-specific resolutions apply.

In all cases the models generated are shuffled using `rng`, unless `shuffle=false`.

See also [`TunedModel`](@ref), [`range`](@ref).
