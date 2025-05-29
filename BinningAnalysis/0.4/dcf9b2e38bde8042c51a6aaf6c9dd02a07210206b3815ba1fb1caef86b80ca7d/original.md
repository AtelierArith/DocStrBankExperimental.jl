```
ErrorPropagator(zero_element::T...[; capacity::Int])
```

Creates a new `ErrorPropagator` which can take (at least) `capacity` many values for each input of type `T`. The type and the size are inherited from the given `zero_element`s, which must exclusively contain zeros.

Values can be added using `push!` and `append!`.

---

```
ErrorPropagator(timeseries::AbstractVector{T}...)
```

Creates a new `ErrorPropagator` and adds all elements from each given timeseries.
