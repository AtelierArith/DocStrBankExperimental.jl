```
NonlinearSolvePolyAlgorithm(algs; start_index::Int = 1)
```

A general way to define PolyAlgorithms for `NonlinearProblem` and `NonlinearLeastSquaresProblem`. This is a container for a tuple of algorithms that will be tried in order until one succeeds. If none succeed, then the algorithm with the lowest residual is returned.

### Arguments

  * `algs`: a tuple of algorithms to try in-order! (If this is not a Tuple, then the returned algorithm is not type-stable).

### Keyword Arguments

  * `start_index`: the index to start at. Defaults to `1`.

### Example

```julia
using NonlinearSolve

alg = NonlinearSolvePolyAlgorithm((NewtonRaphson(), Broyden()))
```
