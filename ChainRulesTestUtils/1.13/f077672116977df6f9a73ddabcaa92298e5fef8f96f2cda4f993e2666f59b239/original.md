```
TestIterator{T,IS<:Base.IteratorSize,IE<:Base.IteratorEltype}
```

A configurable iterator for testing purposes.

```
TestIterator(data, itersize, itereltype)
TestIterator(data)
```

The iterator wraps another iterator `data`, such as an array, that must have at least as many features implemented as the test iterator and have a `FiniteDifferences.to_vec` overload. By default, the iterator it has the same features as `data`.

The optional methods `eltype`, `length`, and `size` are automatically defined and forwarded to `data` if the type arguments indicate that they should be defined.
