```
KahanSum(T::Type = Float64)
```

Track the overall sum. Includes a compensation term that effectively doubles precision, see [Wikipedia](https://en.wikipedia.org/wiki/Kahan_summation_algorithm) for details.

# Example

```
fit!(KahanSum(Float64), fill(1, 100))
```
