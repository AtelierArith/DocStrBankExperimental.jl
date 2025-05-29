```
Series(stats)
Series(stats...)
Series(; stats...)
```

Track a collection stats for one data stream.

# Example

```
s = Series(Mean(), Variance())
fit!(s, randn(1000))
```
