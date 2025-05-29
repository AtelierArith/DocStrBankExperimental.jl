```
Bootstrap(o::OnlineStat, nreps = 100, d = [0, 2])
```

Calculate an online statistical bootstrap of `nreps` replicates of `o`.  For each call to `fit!`, any given replicate will be updated `rand(d)` times (default is double or nothing).

# Example

```
o = Bootstrap(Variance())
fit!(o, randn(1000))
confint(o, .95)
```
