```
dpmap(fn, args...; mod = Main, kwargs...)
```

"Distributed pool map."

A wrapper for `pmap` from `Distributed` package that executes the code in the correct module, so that it can access the distributed variables at remote workers. All arguments other than the first function `fn` are passed to `pmap`.

The function `fn` should return an expression that is going to get evaluated.

# Example

```julia
using Distributed
dpmap(x -> :(computeSomething(someData, $x)), WorkerPool(workers), Vector(1:10))
```

```julia
di = distributeSomeData()
dpmap(x -> :(computeSomething($(di.val), $x)), CachingPool(di.workers), Vector(1:10))
```
