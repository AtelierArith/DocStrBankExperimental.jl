A simple Newton solver for the vector x* such that f(x*) = 0.

The input `x` is the initial guess.

The default `dfdx=nothing` uses `ForwardDiff.jacobian` to compute the jacobian automatically. In this case the output of `f` must be an `AbstractArray`.

`tol` is measured in the vector norm of the change in `x` between successive iterations.
