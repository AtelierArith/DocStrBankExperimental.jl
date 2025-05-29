# LBFGS

## Constructor

```julia
LBFGS(; m::Integer = 10,
alphaguess = LineSearches.InitialStatic(),
linesearch = LineSearches.HagerZhang(),
P=nothing,
precondprep = Returns(nothing),
manifold = Flat(),
scaleinvH0::Bool = true && (typeof(P) <: Nothing))
```

`LBFGS` has two special keywords; the memory length `m`, and the `scaleinvH0` flag. The memory length determines how many previous Hessian approximations to store. When `scaleinvH0 == true`, then the initial guess in the two-loop recursion to approximate the inverse Hessian is the scaled identity, as can be found in Nocedal and Wright (2nd edition) (sec. 7.2).

In addition, LBFGS supports preconditioning via the `P` and `precondprep` keywords.

## Description

The `LBFGS` method implements the limited-memory BFGS algorithm as described in Nocedal and Wright (sec. 7.2, 2006) and original paper by Liu & Nocedal (1989). It is a quasi-Newton method that updates an approximation to the Hessian using past approximations as well as the gradient.

## References

  * Wright, S. J. and J. Nocedal (2006), Numerical optimization, 2nd edition. Springer
  * Liu, D. C. and Nocedal, J. (1989). "On the Limited Memory Method for Large Scale Optimization". Mathematical Programming B. 45 (3): 503–528
