Compute a solution x to the linear system:

(a₀ + a₁ * A)*x = b

using starting guess x₀. Leaving a₀, a₁ set to their default values solves the  system A*x = b.

To adjust the balance between accuracy of solution and speed of the algorithm, it is recommed to first try adjusting the updater keyword arguments as descibed below.

Keyword arguments:

  * `nsweeps`, `cutoff`, `maxdim`, etc. (like for other MPO/MPS updaters).
  * `updater_kwargs=(;)` - a `NamedTuple` containing keyword arguments that will get forwarded to the local updater, in this case `KrylovKit.linsolve` which is a GMRES linear updater. For example:

    ```juli
    linsolve(A, b, x; maxdim=100, cutoff=1e-8, nsweeps=10, updater_kwargs=(; ishermitian=true, tol=1e-6, maxiter=20, krylovdim=30))
    ```

    See `KrylovKit.jl` documentation for more details on available keyword arguments.
