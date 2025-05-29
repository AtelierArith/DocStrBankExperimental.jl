```
optimize_index!(
    index::AbstractSearchIndex,
    context::AbstractContext,
    kind::ErrorFunction=MinRecall(0.9);
    space::AbstractSolutionSpace=optimization_space(index),
    context_exhaustive_search=GenericContext(context),
    queries=nothing,
    ksearch=10,
    numqueries=64,
    initialpopulation=16,
    maxpopulation=16,
    bsize=4,
    mutbsize=16,
    crossbsize=8,
    tol=-1.0,
    maxiters=16,
    verbose=false,
    params=SearchParams(; maxpopulation, bsize, mutbsize, crossbsize, tol, maxiters, verbose)
)
```

Tries to configure the `index` to achieve the specified performance (`kind`). The optimization procedure is an stochastic search over the configuration space yielded by `kind` and `queries`.

# Arguments

  * `index`: the index to be optimized
  * `context`: index context
  * `kind`: The kind of optimization to apply, it can be `ParetoRecall()`, `ParetoRadius()` or `MinRecall(r)` where `r` is the expected recall (0-1, 1 being the best quality but at cost of the search time)

# Keyword arguments

  * `space`: defines the search space
  * `queries`: the set of queries to be used to measure performances, a validation set. It can be an `AbstractDatabase` or nothing.
  * `queries_ksearch`: the number of neighbors to retrieve for `queries`
  * `queries_size`: if `queries===nothing` then a sample of the already indexed database is used, `queries_size` is the size of the sample.
  * `initialpopulation`: the initial sample for the optimization procedure
  * `minbatch`: controls how multithreading is used for evaluating configurations, see [`getminbatch`](@ref)
  * `params`: the parameters of the solver, see [`SearchParams` arguments of `SearchModels.jl`](https://github.com/sadit/SearchModels.jl) package for more information.   Alternatively, you can pass some keywords arguments to `SearchParams`, and use the rest of default values:

      * `initialpopulation=16`: initial sample
      * `minbatch=0`: minimum batch size (`Polyester` multithreading, `0` chooses the size based on the input)
      * `maxpopulation=16`: population upper limit
      * `bsize=4`: beam size (top best elements used by select, mutate and crossing operations.)
      * `mutbsize=16`: number of mutated new elements in each iteration
      * `crossbsize=8`: number of new elements from crossing operation.
      * `maxiters=16`: maximum number of iterations.
      * `verbose`: controls if the procedure is verbose or not
