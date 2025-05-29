```
matopen(filename [, mode]; compress = false) -> handle
matopen(f::Function, filename [, mode]; compress = false) -> f(handle)
```

Mode defaults to `"r"` for read. It can also be `"w"` for write, or `"r+"` for read or write without creation or truncation.

Compression on reading is detected/handled automatically; the `compress` keyword argument only affects write operations.

Use with `read`, `write`, `close`, `keys`, and `haskey`.
