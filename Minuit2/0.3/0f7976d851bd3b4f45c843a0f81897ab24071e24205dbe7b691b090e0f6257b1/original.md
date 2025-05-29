```
migrad!(m::Minuit, strategy=1; ncall=0)
```

Run Migrad minimization.

Migrad from the Minuit2 library is a robust minimisation algorithm which earned its reputation in 40+ years of almost exclusive usage in high-energy physics. How Migrad works is described in the [Minuit]() paper. It uses first and approximate second derivatives to achieve quadratic convergence near the minimum.

## Parameters

  * `m::Minuit` : The Minuit object to minimize.
  * `strategy::Int` : The minimization strategy. The default value is 1, which is   the recommended value for most cases. The value 0 is faster, but less   reliable. The value 2 is slower, but more reliable. The value 3 or higher is slower,   but even more reliable.

## Keyword Parameters

  * `ncall::Int=0` : Approximate upper limit for the number of calls. If set to 0, use the adaptive heuristic from the Minuit2 library.

The following two parameters controls the behavior of [`robust_low_level_fit`](@ref), which essentially tries to restart Migrad procedure when it fails to converge after the first iteration:

  * `iterate::Int=5` : Number of iterations to run the minimization. Default is 5.
  * `use_simplex::Bool=true` : If `true`, use the simplex algorithm in retry to find the minimum. If `false`, use the migrad algorithm.
