# Brent

## Constructor

```julia
    Brent(;)
```

## Description

Also known as the Brent-Dekker algorith, `Brent` is a univariate optimization algorithm for minimizing functions on some interval `[a,b]`. The method uses bisection to find a zero of the gradient. If the original interval contains a minimum, bisection will reliably find the solution, but can be slow. To this end `Brent` combines bisection with the secant method and inverse quadratic interpolation to accelerate convergence.

## References

R. P. Brent (2002) Algorithms for Minimization Without Derivatives. Dover edition.
