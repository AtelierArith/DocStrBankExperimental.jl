```
partition(X, fractions...;
          shuffle=nothing,
          rng=Random.GLOBAL_RNG,
          stratify=nothing,
          multi=false)
```

Splits the vector, matrix or table `X` into a tuple of objects of the same type, whose vertical concatenation is `X`. The number of rows in each component of the return value is determined by the corresponding `fractions` of `length(nrows(X))`, where valid fractions are floats between 0 and 1 whose sum is less than one. The last fraction is not provided, as it is inferred from the preceding ones.

For synchronized partitioning of multiple objects, use the `multi=true` option.

```julia-repl
julia> partition(1:1000, 0.8)
([1,...,800], [801,...,1000])

julia> partition(1:1000, 0.2, 0.7)
([1,...,200], [201,...,900], [901,...,1000])

julia> partition(reshape(1:10, 5, 2), 0.2, 0.4)
([1 6], [2 7; 3 8], [4 9; 5 10])

julia> X, y = make_blobs() # a table and vector
julia> Xtrain, Xtest = partition(X, 0.8, stratify=y)
```

Here's an example of synchronized partitioning of multiple objects:

```julia-repl
julia> (Xtrain, Xtest), (ytrain, ytest) = partition((X, y), 0.8, rng=123, multi=true)
```

## Keywords

  * `shuffle=nothing`: if set to `true`, shuffles the rows before taking fractions.
  * `rng=Random.GLOBAL_RNG`: specifies the random number generator to be used, can be an integer seed. If specified, and `shuffle === nothing` is interpreted as true.
  * `stratify=nothing`: if a vector is specified, the partition will match the stratification of the given vector. In that case, `shuffle` cannot be `false`.
  * `multi=false`: if `true` then `X` is expected to be a `tuple` of objects sharing a common length, which are each partitioned separately using the same specified `fractions` *and* the same row shuffling. Returns a tuple of partitions (a tuple of tuples).
