```
unique_points(vectors; distance = EuclideanNorm(), atol = 1e-14, rtol = 1e-8, kwargs...)
```

Returns all elements in `vector` for which two elements have `distance` at most `max(atol, rtol * distance(0,w[i]))`. Note that the output can depend on the order of elements in vectors. The remaining `kwargs` are things that can be passed to [`UniquePoints`](@ref).
