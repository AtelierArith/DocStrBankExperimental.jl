```
SPGBoxResult
```

Data structure that contains the results of the `spgbox` optimization method. 

```
`x`: Array containing final point (solution or best point found).

`f`: Final objective function value.

`gnorm`: Norm of the projected gradient on the bounds.

`nit`: Number of iterations performed. 

`nfeval`: Number of function evaluations.

`ierr`: Status of execution: 

     0. Converged successfully to solution. 

     1. Maximum number of iterations achieved.

     2. Maximum number of function evaluations achieved.

`return_from_callback`: Boolean indicating if the algorithm returned from the callback function.
```
