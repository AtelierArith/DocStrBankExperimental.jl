```
has_standard_indexing(A)
```

return `true` if the indices of `A` start with 1 along all axes. Can be called with multiple arguments:

```
has_standard_indexing(A, B, ...)
```

is equivalent to:

```
has_standard_indexing(A) && has_standard_indexing(B) && ...
```

Opposite of `Base.has_offset_axes` which is not available in version of Julia older than 0.7.
