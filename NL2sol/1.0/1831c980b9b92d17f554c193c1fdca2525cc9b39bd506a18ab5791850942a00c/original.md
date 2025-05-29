```
nl2sol solves the non-linear least squares problem.  That is, it finds
an x that minimizes  sum(i=1:n){r_i(x)^2} where x is a vector of size p.
It returns a struct of type Optim.MultivariateOptimizationResults that
contains the relevant info (see the Optim docs for further info)

The residual and the jacobian functions are expected to take args that
have been preallocated for those values.  These arrays are actually 
allocated in the Julia function nl2sol before passing to the Fortran
subroutine nl2sol.

NOTE: NL2sol.jl does pointer tricks in order to interface with the
      FORTRAN code, so tread lightly if you'd like to modify the code.

EXAMPLE USAGE

using NL2sol

function rosenbrock_res(x, r)
    r[1] = 10. * (x[2] - x[1]^2 )
    r[2] = 1. - x[1]
    return r
end

function rosenbrock_jac(x, jac)
    jac[1, 1] = -20.0 * x[1]
    jac[1, 2] =  10.0
    jac[2, 1] =  -1.0
    jac[2, 2] =   0.0
   return jac
end

function main()
    println("NL2SOL on Rosenbrock")
    result = nl2sol(rosenbrock_res, rosenbrock_jac, [-1.2, 1.0], 2; quiet=true)
    println(result)
end

main()
```
