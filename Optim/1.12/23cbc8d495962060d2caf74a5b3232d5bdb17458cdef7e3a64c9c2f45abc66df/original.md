# BFGS

## Constructor

```julia
BFGS(; alphaguess = LineSearches.InitialStatic(),
       linesearch = LineSearches.HagerZhang(),
       initial_invH = x -> Matrix{eltype(x)}(I, length(x), length(x)),
       manifold = Flat())
```

## Description

The `BFGS` method implements the Broyden-Fletcher-Goldfarb-Shanno algorithm as described in Nocedal and Wright (sec. 8.1, 1999) and the four individual papers Broyden (1970), Fletcher (1970), Goldfarb (1970), and Shanno (1970). It is a quasi-Newton method that updates an approximation to the Hessian using past approximations as well as the gradient. See also the limited memory variant `LBFGS` for an algorithm that is more suitable for high dimensional problems.

## References

  * Wright, S. J. and J. Nocedal (1999), Numerical optimization. Springer Science 35.67-68: 7.
  * Broyden, C. G. (1970), The convergence of a class of double-rank minimization algorithms, Journal of the Institute of Mathematics and Its Applications, 6: 76–90.
  * Fletcher, R. (1970), A New Approach to Variable Metric Algorithms, Computer Journal, 13 (3): 317–322,
  * Goldfarb, D. (1970), A Family of Variable Metric Updates Derived by Variational Means, Mathematics of Computation, 24 (109): 23–26,
  * Shanno, D. F. (1970), Conditioning of quasi-Newton methods for function minimization, Mathematics of Computation, 24 (111): 647–656.
