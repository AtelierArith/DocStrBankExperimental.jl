```
ITensor([ElT::Type, ]x::Number, inds)
ITensor([ElT::Type, ]x::Number, inds::Index...)
```

Construct an ITensor with all elements set to `x` and indices `inds`.

If `x isa Int` or `x isa Complex{Int}` then the elements will be set to `float(x)`   unless specified otherwise by the first input.

The storage will have `NDTensors.Dense` type.

# Examples

```julia   i = Index(2,"index*i"); j = Index(4,"index*j"); k = Index(3,"index_k");

A = ITensor(1.0, i, j)   A = ITensor(1, i, j) # same as above   B = ITensor(2.0+3.0im, j, k)   ```

!!! warning       In future versions this may not automatically convert integer inputs with `float`, and in that case the particular element type should not be relied on.
