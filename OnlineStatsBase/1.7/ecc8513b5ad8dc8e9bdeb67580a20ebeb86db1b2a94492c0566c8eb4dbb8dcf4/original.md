```
Group(stats::OnlineStat...)
Group(; stats...)
Group(collection)
```

Create a vector-input stat from several scalar-input stats.  For a new observation `y`, `y[i]` is sent to `stats[i]`.

# Examples

```
x = randn(100, 2)

fit!(Group(Mean(), Mean()), eachrow(x))
fit!(Group(Mean(), Variance()), eachrow(x))

o = fit!(Group(m1 = Mean(), m2 = Mean()), eachrow(x))
o.stats.m1
o.stats.m2

o = Group(fill(Mean(), 10))
fit!(o, eachrow(randn(100, 10)))
```
