```
splitobs(data, [at = 0.7], [obsdim]) -> Tuple
```

Split the `data` into multiple subsets proportional to the value(s) of `at`.

Note that this function will perform the splits statically and thus not perform any randomization. The function creates a `NTuple` of data subsets in which the first N-1 elements/subsets contain the fraction of observations of `data` that is specified by `at`.

For example, if `at` is a `Float64` then the return-value will be a tuple with two elements (i.e. subsets), in which the first element contains the fracion of observations specified by `at` and the second element contains the rest. In the following code the first subset `train` will contain the first 70% of the observations and the second subset `test` the rest.

```julia
train, test = splitobs(X, at = 0.7)
```

If `at` is a tuple of `Float64` then additional subsets will be created. In this example `train` will have the first 50% of the observations, `val` will have next 30%, and `test` the last 20%

```julia
train, val, test = splitobs(X, at = (0.5, 0.3))
```

It is also possible to call `splitobs` with multiple data arguments as tuple, which all must have the same number of total observations. This is useful for labeled data.

```julia
train, test = splitobs((X, y), at = 0.7)
(x_train,y_train), (x_test,y_test) = splitobs((X, y), at = 0.7)
```

If the observations should be randomly assigned to a subset, then you can combine the function with `shuffleobs`

```julia
# This time observations are randomly assigned.
train, test = splitobs(shuffleobs((X,y)), at = 0.7)
```

When working with arrays one may want to choose which dimension represents the observations. By default the last dimension is assumed, but this can be overwritten.

```julia
# Here we say each row represents an observation
train, test = splitobs(X, obsdim = 1)
```

The functions also provide a type-stable API

```julia
# By avoiding keyword arguments, the compiler can infer the return type
train, test = splitobs((X,y), 0.7)
train, test = splitobs((X,y), 0.7, ObsDim.First())
```

see [`DataSubset`](@ref) for more information on data subsets.

see [`stratifiedobs`](@ref) for a related function that preserves the target distribution.
