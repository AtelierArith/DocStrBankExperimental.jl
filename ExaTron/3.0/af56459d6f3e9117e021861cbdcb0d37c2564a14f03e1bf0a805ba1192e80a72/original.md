Subroutine dtron

This subroutine implements a trust region Newton method for the solution of large bound-constrained optimization problems

min { f(x) : xl <= x <= xu }

where the Hessian matrix is sparse. The user must evaluate the function, gradient, and the Hessian matrix.
