# Example calls

```
xstar, fval, exitflag, info = DAQPBase.quadprog(H,f,A,bupper)
xstar, fval, exitflag, info = DAQPBase.quadprog(H,f,A,bupper,blower,sense)
```

finds the solution `xstar` to the quadratic program

```
 minimize	   0.5 x' H x + f' x
subject to   blower <= A x <= bupper
```

If `bupper` and `blower` have more elements than rows of `A`, the first elements are interpreted as simple bounds. For example:

```
    A = [7.0 8.0]
    blower = [-4.0; -5.0; -6.0]
    bupper = [ 1.0;  2.0;  3.0]
```

is interpreted as

```
        -4.0 <= x₁ <= 1.0
        -5.0 <= x₂ <= 2.0
    -6.0 <= 7 x₁ + 8 x₂ <= 3.0

```

# Input

  * `H`           - cost matrix
  * `f`           - cost vector
  * `A`           - linear constraint matrix
  * `buppe`       - upper bounds for constraints
  * `blower`      - lower bounds for constraints (default: -Inf)
  * `sense`       - constraint types, as a vector of Cints (default: 0). Example types:

      * `0` : inequality
      * `1` : active inequality (used as warm start)
      * `5` : equality
      * `8` : soft (allowed to be violated if necessary)
      * `16` : binary (either upper or lower bound should hold with equality)

# Output

  * `xstar`       - solution
  * `fval`        - objective function value for `xstar`.
  * `exitflag`    - flag from solver (>0 success, <0 failure)
  * `info`        - tuple containing profiling information from the solver.
