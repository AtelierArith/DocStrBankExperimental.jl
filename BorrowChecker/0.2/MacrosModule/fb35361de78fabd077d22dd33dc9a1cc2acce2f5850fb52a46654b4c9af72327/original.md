```
@own [:mut] x = value
@own [:mut] x, y, z = (value1, value2, value3)
@own [:mut] for var in iter
    # body
end
@own [:mut] x  # equivalent to @own [:mut] x = x
@own [:mut] (x, y)  # equivalent to @own [:mut] (x, y) = (x, y)
```

Create a new owned variable. If `:mut` is specified, the value will be mutable. Otherwise, the value will be immutable.

You may also use `@own` in a `for` loop to create an owned value for each iteration.
