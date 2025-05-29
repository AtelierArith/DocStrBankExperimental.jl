```
chebregression(x, y, [lb, ub,] order)
```

Return a Chebyshev polynomial (`ChebPoly`) constructed by performing a least-square fit of Chebyshev polnomials of the given `order`, where `x` are the coordinates of the data points `y`.  `lb` and `ub` are the lower and upper bounds, respectively, of the Chebyshev domain; these should normally enclose all of the points in `x`, and default to the minimum and maximum coordinates in `x` if they are omitted.

In the 1d case, `x` is an array of scalars, `lb < ub` are scalars, and `order` is an integers.   In the `N`-dimensional case, `order` is an `N`-tuple of integers (the order in each dimension), `lb` and `ub` are `N`-component vectors, and `x` is an array of `N`-component vectors (or a matrix with `N` columns, interpreted as the vector components).

`y` can be a vector or numbers or a vector of vectors (for vector- valued Chebyshev fits).  The latter case can also be input as a matrix whose columns are the vector componnents.  `size(x,1)` and `size(y,1)` must match, and must exceed `prod(order .+ 1)`.
