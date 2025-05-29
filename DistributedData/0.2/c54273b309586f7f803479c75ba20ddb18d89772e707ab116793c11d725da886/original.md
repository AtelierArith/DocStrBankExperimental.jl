```
dmapreduce(val, map, fold, workers; prefetch = :all)
```

A distributed work-alike of the standard `mapreduce`: Take a function `map` (a non-modifying transform on the data) and `fold` (2-to-1 reduction of the results of `map`), systematically run them on the data described by `val` distributed on `workers`, and return the final reduced result.

It is assumed that the fold operation is associative, but not commutative (as in semigroups). If there are no workers, operation returns `nothing` (we don't have a monoid to magically conjure zero elements :[ ).

In the current version, the reduce step is a sequential left fold, executed in the main process. Parameter `prefetch` says how many futures should be `fetch`ed in advance; increasing prefetch improves the throughput but increases memory usage in case the results of `map` are big.

# Example

```
# compute the mean of all distributed data
sum,len = dmapreduce(:myData,
    (d) -> (sum(d),length(d)),
    ((s1, l1), (s2, l2)) -> (s1+s2, l1+l2),
    workers())
println(sum/len)
```

# Processing multiple arguments (a.k.a. "zipWith")

The `val` here does not necessarily need to refer to a symbol, you can easily pass in a quoted tuple, which will be unquoted in the function parameter. For example, distributed values `:a` and `:b` can be joined as such:

```
dmapreduce(:((a,b)),
    ((a,b)::Tuple) -> [a b],
    vcat,
    workers())
```
