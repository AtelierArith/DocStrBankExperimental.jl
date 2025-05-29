```
divides(t1::AbstractTermLike, t2::AbstractTermLike)
```

Returns whether the monomial of t1 divides the monomial of t2.

### Examples

Calling `divides(2x^2y, 3xy)` should return false because `x^2y` does not divide `xy` since `x` has a degree 2 in `x^2y` which is greater than the degree of `x` on `xy`. However, calling `divides(3xy, 2x^2y)` should return true.
