```
StatLag(stat, b)
```

Track a moving window (previous `b` copies) of `stat`.

# Example

```
fit!(StatLag(Mean(), 10), 1:20)
```
