```
MovingWindow(b, T)
MovingWindow(T, b)
```

Track a moving window of `b` items of type `T`.  Also known as a circular buffer.

# Example

```
o = MovingWindow(10, Int)
fit!(o, 1:14)
```
