```
xstar, fval, exitflag, info = DAQPBase.linprog(f,A,bupper)
xstar, fval, exitflag, info = DAQPBase.linprog(f,A,bupper,blower,sense)
```

finds the solution `xstar` to the linear program

```
min_x	f' x
subject to 
    blower[1:ms]	<= x[1:ms] <= bupper[1:ms]
    blower[ms+1:m]  <= A*x 	   <= bupper[ms+1:m],
```

where `m = length(bupper)` and `ms = m-size(A,2)`.

# Input

  * `f`  			- linear term in objective function, n-vector
  * `A`  			- constraint normals, (`(m-ms) x n`)-matrix
  * `bupper` 		- upper bounds for constraints, `m`-vector
  * `blower` 		- lower bounds for constraints, `m`-vector (default: -Inf)
  * `sense` 		- constraint types,  `m`-vector of Cints (default: 0). Example types:

      * `0` : inequality
      * `5` : equality

# Output

  * `xstar` 		- solution provided by solver
  * `fval` 		- objective function value for `xstar`.
  * `exitflag` 	- flag from solver (>0 success, <0 failure)
  * `info` 		- tuple containing profiling information from the solver.
