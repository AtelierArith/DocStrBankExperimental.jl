```
apply!(buffer::I, tfm, item::I)
```

Applies `tfm` to `item`, mutating the preallocated `buffer`.

`buffer` can be obtained with `buffer = makebuffer(tfm, item)`

```
apply!(buffer, tfm::Transform, item::I; randstate) = apply(tfm, item; randstate)
```

Default to `apply(tfm, item)` (non-mutating version).
