```
minimise(f, X, structure = SortedVector, tol=1e-3)
or
minimise(f, X, structure = HeapedVector, tol=1e-3)
or
minimise(f, X, tol=1e-3) in this case the default value of "structure" is "HeapedVector"
```

Find the global minimum of the function `f` over the `Interval` or `IntervalBox` `X` using the Moore-Skelboe algorithm. The way in which vector elements are kept arranged can be either a heaped array or a sorted array. If you not specify any particular strategy to keep vector elements arranged then by default heaped array is used.

For higher-dimensional functions $f:\mathbb{R}^n \to \mathbb{R}$, `f` must take a single vector argument.

Returns an interval containing the global minimum, and a list of boxes that contain the minimisers.
