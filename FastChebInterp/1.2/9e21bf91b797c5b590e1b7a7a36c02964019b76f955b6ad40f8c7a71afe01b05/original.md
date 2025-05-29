```
chebpoints(order, lb, ub)
```

Return an array of Chebyshev points (as `SVector` values) for the given `order` (an array or tuple of polynomial degrees), and hypercube lower-and upper-bound vectors `lb` and `ub`. If `ub` and `lb` are numbers, returns an array of numbers.

These are the points where you should evaluate a function in order to create a Chebyshev interpolant with `chebinterp`.

(Note that the number of points along each dimension is `1 +` the order in that direction.)
