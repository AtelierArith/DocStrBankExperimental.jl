# Newton

## Constructor

```julia
Newton(; alphaguess = LineSearches.InitialStatic(),
linesearch = LineSearches.HagerZhang())
```

## Description

The `Newton` method implements Newton's method for optimizing a function. We use a special factorization from the package `PositiveFactorizations.jl` to ensure that each search direction is a direction of descent. See Wright and Nocedal and Wright (ch. 6, 1999) for a discussion of Newton's method in practice.

## References

  * Nocedal, J. and S. J. Wright (1999), Numerical optimization. Springer Science 35.67-68: 7.
