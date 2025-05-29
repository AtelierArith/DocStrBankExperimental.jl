```
merge!(a, b)
```

Merge `OnlineStat` `b` into `a` (supported by most `OnlineStat` types).

# Example

```
a = fit!(Mean(), 1:10)
b = fit!(Mean(), 11:20)
merge!(a, b)
```
