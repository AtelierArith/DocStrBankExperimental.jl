```
CircBuff(T, b; rev=false)
```

Create a fixed-length circular buffer of `b` items of type `T`.

  * `rev=false`: `o[1]` is the oldest.
  * `rev=true`: `o[end]` is the oldest.

# Example

```
a = CircBuff(Int, 5)
b = CircBuff(Int, 5, rev=true)

fit!(a, 1:10)
fit!(b, 1:10)

a[1] == b[end] == 1
a[end] == b[1] == 10

value(o; ordered=false)  # Retrieve values (no copy) without ordering
```
