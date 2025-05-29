```
Lag(T, b::Int)
```

Store the last `b` values for a data stream of type `T`.  Values are stored as

$v(t), v(t-1), v(t-2), …, v(t-b+1)$

so that `value(o::Lag)[1]` is the most recent observation and `value(o::Lag)[end]` is the `b`-th most recent observation.

# Example

```
o = fit!(Lag(Int, 10), 1:12)
o[1]
o[end]
```
