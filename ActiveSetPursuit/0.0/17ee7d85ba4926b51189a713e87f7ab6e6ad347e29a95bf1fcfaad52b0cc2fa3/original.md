`julia     function bpdual(A, b, λin, bl, bu; kwargs...)` 

````
Solve the optimization problem:

DP:
```math 
    \min_{y} \left( -b^T y + \frac{1}{2} λ y^T y \right)
```
    subject to:
 ```math 
    bl \leq A^T y \leq bu
    ```

using given `A`, `b`, `bl`, `bu`, and `λ`. When `bl = -e` and `bu = e = ones(n, 1)`,
DP is the dual Basis Pursuit problem:

BPdual:

```math 
\max_{y} \left( b^T y - \frac{1}{2} λ y^T y \right)
```
    subject to
    
```math
    \|A^T y\|_{\infty} \leq 1.
```

* Input
* `A` : `m`-by-`n` explicit matrix or linear operator.
* `b` : `m`-vector.
* `λin` : Nonnegative scalar.
* `bl`, `bu` : `n`-vectors (bl lower bound, bu upper bound).
* `active`, `state`, `y`, `S`, `R` : May be empty or output from `BPdual` with a previous value of `λ`.
* `loglevel` : Logging level.
* `coldstart` : Boolean indicating if a cold start should be used.
* `homotopy` : Boolean indicating if homotopy should be used.
* `λmin` : Minimum value for `λ`.
* `trim` : Number of constraints to trim.
* `itnMax` : Maximum number of iterations.
* `feaTol` : Feasibility tolerance.
* `optTol` : Optimality tolerance.
* `gapTol` : Gap tolerance.
* `pivTol` : Pivot tolerance.
* `actMax` : Maximum number of active constraints.

* Output
* `tracer` : A structure to store trace information at each iteration of the optimization process.
    It contains:
        * `active::Vector{Int}`: The indices of the active constraints.
        * `activesoln::Vector{T}`: The solutions corresponding to the current active set.
        * `lambda::Vector{T}`: Lambda values.
        * `N::Int`: The total number of variables in the solution vector.
````
