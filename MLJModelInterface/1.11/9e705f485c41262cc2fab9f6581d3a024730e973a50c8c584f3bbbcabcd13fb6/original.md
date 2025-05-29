```
UnivariateFinite(
    support,
    probs;
    pool=nothing,
    augmented=false,
    ordered=false
)
```

Construct a discrete univariate distribution whose finite support is the elements of the vector `support`, and whose corresponding probabilities are elements of the vector `probs`. Alternatively, construct an abstract *array* of `UnivariateFinite` distributions by choosing `probs` to be an array of one higher dimension than the array generated.

Here the word "probabilities" is an abuse of terminology as there is no requirement that probabilities actually sum to one, only that they be non-negative. So `UnivariateFinite` objects actually implement arbitrary non-negative measures over finite sets of labelled points. A `UnivariateDistribution` will be a bona fide probability measure when constructed using the `augment=true` option (see below) or when `fit` to data.

Unless `pool` is specified, `support` should have type `AbstractVector{<:CategoricalValue}` and all elements are assumed to share the same categorical pool, which may be larger than `support`.

*Important.* All levels of the common pool have associated probabilities, not just those in the specified `support`. However, these probabilities are always zero (see example below).

If `probs` is a matrix, it should have a column for each class in `support` (or one less, if `augment=true`). More generally, `probs` will be an array whose size is of the form `(n1, n2, ..., nk, c)`, where `c = length(support)` (or one less, if `augment=true`) and the constructor then returns an array of `UnivariateFinite` distributions of size `(n1, n2, ..., nk)`.

## Examples

```julia-repl
julia> v = categorical(["x", "x", "y", "x", "z"])
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "x"
 "x"
 "y"
 "x"
 "z"

julia> UnivariateFinite(classes(v), [0.2, 0.3, 0.5])
UnivariateFinite{Multiclass{3}}(x=>0.2, y=>0.3, z=>0.5)

julia> d = UnivariateFinite([v[1], v[end]], [0.1, 0.9])
UnivariateFinite{Multiclass{3}}(x=>0.1, z=>0.9)

julia> rand(d, 3)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "x"
 "z"
 "x"

julia> levels(d)
3-element Vector{String}:
 "x"
 "y"
 "z"

julia> pdf(d, "y")
0.0

```

### Specifying a pool

Alternatively, `support` may be a list of raw (non-categorical) elements if `pool` is:

  * some `CategoricalArray`, `CategoricalValue` or `CategoricalPool`, such that `support` is a subset of `levels(pool)`
  * `missing`, in which case a new categorical pool is created which has `support` as its only levels.

In the last case, specify `ordered=true` if the pool is to be considered ordered.

```julia-repl
julia> UnivariateFinite(["x", "z"], [0.1, 0.9], pool=missing, ordered=true)
UnivariateFinite{OrderedFactor{2}}(x=>0.1, z=>0.9)

julia> d = UnivariateFinite(["x", "z"], [0.1, 0.9], pool=v) # v defined above
UnivariateFinite{Multiclass{3}}(x=>0.1, z=>0.9)

julia> pdf(d, "y") # allowed as `"y" in levels(v)`
0.0

julia> v = categorical(["x", "x", "y", "x", "z", "w"])
6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "x"
 "x"
 "y"
 "x"
 "z"
 "w"

julia> probs = rand(100, 3); probs = probs ./ sum(probs, dims=2);

julia> UnivariateFinite(["x", "y", "z"], probs, pool=v)
100-element UnivariateFiniteVector{Multiclass{4}, String, UInt32, Float64}:
 UnivariateFinite{Multiclass{4}}(x=>0.194, y=>0.3, z=>0.505)
 UnivariateFinite{Multiclass{4}}(x=>0.727, y=>0.234, z=>0.0391)
 UnivariateFinite{Multiclass{4}}(x=>0.674, y=>0.00535, z=>0.321)
 ⋮
 UnivariateFinite{Multiclass{4}}(x=>0.292, y=>0.339, z=>0.369)
```

### Probability augmentation

If `augment=true` the provided array is augmented by inserting appropriate elements *ahead* of those provided, along the last dimension of the array. This means the user only provides probabilities for the classes `c2, c3, ..., cn`. The class `c1` probabilities are chosen so that each `UnivariateFinite` distribution in the returned array is a bona fide probability distribution.

---

```
UnivariateFinite(prob_given_class; pool=nothing, ordered=false)
```

Construct a discrete univariate distribution whose finite support is the set of keys of the provided dictionary, `prob_given_class`, and whose values specify the corresponding probabilities.

The type requirements on the keys of the dictionary are the same as the elements of `support` given above with this exception: if non-categorical elements (raw labels) are used as keys, then `pool=...` must be specified and cannot be `missing`.

If the values (probabilities) are arrays instead of scalars, then an abstract array of `UnivariateFinite` elements is created, with the same size as the array.
