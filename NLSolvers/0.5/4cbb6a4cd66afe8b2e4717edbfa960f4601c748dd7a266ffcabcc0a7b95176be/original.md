```
Backtracking
```

An object that controls the backtracking line search algorithm. The algorithm tries out an initial point and then it iteratively tries to find a good enough step length as measured by the improvement compared to a first order Taylor approximation around a step length of zero.

```
Backtracking(; kwargs...)
```

The `Backtracking` constructor takes the following keyword arguments:

  * `ratio`: the ratio between the current trial step length and the next. This controls how much time is spent looking for a large step size. A common choice is 1/2, which is the default here.
  * `decrease`: a positive threshold less than `ratio` that determines when descent is sufficient. The default value is 0.0001.
  * `maxiter`: maximum number of times to search for a better step length. The default value is 26. With no interpolation and a ratio of 1/2, this means that the search is terminated when the step size reaches `sqrt(eps(Float64))`.
  * `interp`: which type of interpolation to use, if any. Defaults to `FixedInterp()`, i.e. no interpolation.
  * `steprange`: the allowed range for steps lengths, given as a tuple or named tuple. The default is `(; lower=0, upper=Inf)`.
  * `verbose`: if `true`, information about the search is printed as the algorithm progresses. Defaults to `false`.

!!! note
    When chosing parameters, it's important to note that it must be true that `0 < decrease < ratio`.

