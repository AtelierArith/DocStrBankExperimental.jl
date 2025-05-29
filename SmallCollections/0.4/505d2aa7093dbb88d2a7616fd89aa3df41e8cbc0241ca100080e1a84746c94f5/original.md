```
SmallCollections.bitsize(T::Type) -> Int
SmallCollections.bitsize(x::T) where T -> Int
```

Return the size of the internal binary representation of `T` in bits. For `Bool` the function returns `1`.

See also `Base.sizeof`.
