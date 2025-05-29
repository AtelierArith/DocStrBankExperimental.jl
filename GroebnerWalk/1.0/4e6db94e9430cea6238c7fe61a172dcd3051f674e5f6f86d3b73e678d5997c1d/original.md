```
newell_patch_with_orderings(k::Field, n::Int=1)
```

Let $n$ be an integer between 1 and 32. Returns the ideal corresponding to  the implicitization of the $n$-th bi-cubic patch describing the Newell's teapot as a parametric surface. Additionally returns suitable start and target orderings, e.g. for use with the Gröbner walk.

The specific generators for each patch have been taken from [Tran:2004](@cite).

For fields $k\neq\mathbb{Q},\bar{\mathbb{Q}}$, this gives a variant of the ideal with  integer coefficients.
