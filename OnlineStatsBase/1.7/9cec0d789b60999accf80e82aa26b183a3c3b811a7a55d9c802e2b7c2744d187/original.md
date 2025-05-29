```
Extrema(T::Type = Float64)
Extrema(min_init::T, max_init::T)
```

Maximum and minimum (and number of occurrences for each) for a data stream of type `T`.

# Example

```
Extrema(Float64) == Extrema(Inf, -Inf)

o = fit!(Extrema(), rand(10^5))
extrema(o)
maximum(o)
minimum(o)
```
