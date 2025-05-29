# Gradient Descent

## Constructor

```julia
GradientDescent(; alphaguess = LineSearches.InitialHagerZhang(),
linesearch = LineSearches.HagerZhang(),
P = nothing,
precondprep = Returns(nothing),
manifold = Flat())
```

Keywords are used to control choice of line search, and preconditioning.

## Description

The `GradientDescent` method is a simple gradient descent algorithm, that is the search direction is simply the negative gradient at the current iterate, and then a line search step is used to compute the final step. See Nocedal and Wright (ch. 2.2, 1999) for an explanation of the approach.

## References

  * Nocedal, J. and Wright, S. J. (1999), Numerical optimization. Springer Science 35.67-68: 7.
