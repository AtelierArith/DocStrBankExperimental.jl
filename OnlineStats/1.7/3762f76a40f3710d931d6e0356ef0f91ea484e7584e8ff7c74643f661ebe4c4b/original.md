```
Diff(T::Type = Float64)
```

Track the difference and the last value.

# Example

```
o = Diff()
fit!(o, [1.0, 2.0])
last(o)
diff(o)
```
