```
GroupBy(T, stat)
```

Update `stat` for each group (of type `T`).  A single observation is either a (named) tuple with two elements or a Pair.

# Example

```
x = rand(Bool, 10^5)
y = x .+ randn(10^5)
fit!(GroupBy(Bool, Series(Mean(), Extrema())), zip(x,y))
```
