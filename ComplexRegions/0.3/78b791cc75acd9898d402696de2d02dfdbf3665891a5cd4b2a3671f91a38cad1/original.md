```
discretize(p, n)
```

Discretize a path or curve at `n` points, roughly equidistributed by arc length. All vertices are also included.

Returns a tuple of vectors `t` and `z` such that `z[j]` is the point on the curve at parameter value `t[j]`.
