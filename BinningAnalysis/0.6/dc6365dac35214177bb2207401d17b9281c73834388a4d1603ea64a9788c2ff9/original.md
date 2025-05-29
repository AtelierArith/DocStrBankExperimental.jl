```
LogBinner(zero_element::T[; capacity::Int])
```

Creates a new `LogBinner` which can take (at least) `capacity` many values of type `T`. The type and the size are inherited from the given `zero_element`, which must exclusively contain zeros.

Values can be added using `push!` and `append!`.

---

```
LogBinner(timeseries::AbstractVector{T})
```

Creates a new `LogBinner` and adds all elements from the given timeseries.
