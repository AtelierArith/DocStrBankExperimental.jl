```
power_iterations(AᴴA; rtol=1e-3, maxiter=30, verbose=false)
```

Power iterations to determine the maximum eigenvalue of a normal operator or square matrix. For custom AᴴA which are not an abstract array or an `AbstractLinearOperator` one can pass a vector `b` of `size(AᴴA, 2)` to be used during the computation. 

# Arguments

  * `AᴴA`                 - operator or matrix; has to be square
  * b                     - (optional), vector to be used during computation

# Keyword Arguments

  * `rtol=1e-3`           - relative tolerance; function terminates if the change of the max. eigenvalue is smaller than this values
  * `maxiter=30`          - maximum number of power iterations
  * `verbose=false`       - print maximum eigenvalue if `true`

# Output

maximum eigenvalue of the operator
