```
CountMinSketch(T = Number; nhash=50, hashlength=1000, storagetype=Int)
```

Create a Count-Min Sketch with `nhash` hash functions of width `hashlength`.  Counts in the sketch will be stored as `storagetype`.

This lets you calculate an upper bound on the number of occurrences of some value `x` in a data stream via `value(count_min_sketch, x)`.  For details and error bounds, please see the references section.

# Example

```
o = CountMinSketch()

y = rand(1:100, 10^6)

fit!(o, y)

value(o, 1)

sum(y .== 1)
```

# References

  * https://florian.github.io/count-min-sketch/
