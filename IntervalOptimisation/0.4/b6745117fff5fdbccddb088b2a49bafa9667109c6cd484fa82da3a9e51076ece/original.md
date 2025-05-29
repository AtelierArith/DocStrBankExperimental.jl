```
maximise(f, X, structure = SortedVector, tol=1e-3)
or
maximise(f, X, structure = HeapedVector, tol=1e-3)
or
maximise(f, X, tol=1e-3) in this case the default value of "structure" is "HeapedVector"
```

Find the global maximum of the function `f` over the `Interval` or `IntervalBox` `X` using the Moore-Skelboe algorithm. See [`minimise`](@ref) for a description of the available options.
