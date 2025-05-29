```
LogSumExp(T::Type = Float64)
```

For positive numbers that can be very small (or very large), it's common to store each `log(x)` instead of each `x` itself, to avoid underflow (or overflow). `LogSumExp` takes values in this representation and adds them, returning the result in the same representation.

Ref: [https://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html](https://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html)

# Example

```
x = randn(1000)

fit!(LogSumExp(), x)

log(sum(exp.(x))) # should be very close
```
