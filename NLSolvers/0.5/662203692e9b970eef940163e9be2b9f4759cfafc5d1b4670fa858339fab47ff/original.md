# ActiveBox

## Constructor

```julia
    ActiveBox(; factorize = cholesky, epsilon = 1e-8)
```

`factorize` is a function that factorizes the restricted Hessian, `epsilon` determines the threshold for whether a bound is approximately active or not, see eqn. (32) in [1].

## Description

ActiveBox second order for bound constrained convex optimization. It's an active set and allows for rapid exploration of the constraint face. It employs a modified Armijo-line search that takes the active set into account. Details can be found in [1].

## References

  * 1. http://www.mit.edu/~dimitrib/ProjectedNewton.pdf
  * 2. Iterative Methods for Optimization https://archive.siam.org/books/textbooks/fr18_book.pdf
