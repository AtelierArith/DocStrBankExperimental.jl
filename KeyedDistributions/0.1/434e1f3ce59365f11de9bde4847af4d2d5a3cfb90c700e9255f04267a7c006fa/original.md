```
KeyedDistributions.KeyedDistribution(d<:Distributions.Distribution, keys::Tuple{Vararg{AbstractVector}})
KeyedDistributions.KeyedDistribution(d<:Distributions.Distribution; named_keys...)
```

Stores the `keys` (and dimnames if using `named_keys` kwargs) for each variate alongside the `Distributions.Distribution` `d`, supporting all of the common functions of a `Distributions.Distribution` and `KeyedArray`.

Common functions that return an `AbstractArray`, such as `rand`, will return a `KeyedArray` with keys and dimnames derived from the `Distributions.Distribution`.

The type of `keys` is restricted to be consistent with [AxisKeys.jl](https://github.com/mcabbott/AxisKeys.jl). The length of the `keys` tuple or number of `named_keys` must equal the number of dimensions, which is 1 for univariate and multivariate distributions, and 2 for matrix-variate distributions. The length of each key vector in must match the length along each dimension.

!!! note
    For distributions that can be marginalised exactly, the KeyedDistributions.KeyedDistribution can be marginalised via the indexing or lookup syntax just like `KeyedArray`s. i.e. One can use square or round brackets to retain certain indices or keys and marginalise out the others. For example for `D::KeyedMvNormal` over `:a, :b, :c`:

      * `D(:a)` or D[1] will marginalise out `:b, :c` and return a `KeyedNormal` over `:a`.
      * `D([:a])` or D[[1]] will marginalise out `:b, :c` and return a `KeyedMvNormal` over `:a`.
      * `D([:a, :b])` or `D[[1, 2]]` will marginalise out `:c` and return a `KeyedMvNormal` over `:a, :b`.

