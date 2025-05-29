```
overapproximate(S::LazySet, ::Type{<:Interval})
```

Return the overapproximation of a set with an interval.

### Input

  * `S`        – one-dimensional set
  * `Interval` – target type

### Output

An interval.

### Algorithm

We use the `extrema` function.
