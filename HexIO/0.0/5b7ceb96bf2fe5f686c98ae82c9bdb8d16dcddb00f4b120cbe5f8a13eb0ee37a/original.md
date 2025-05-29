```
unpack(io::IO, T::Type, endianness::Symbol = :NativeEndian)
```

Given an input `io`, unpack type `T`, byte-swapping according to the given `endianness` of `io`. If `endianness` is `:NativeEndian` (the default), no byteswapping will occur.  If `endianness` is `:LittleEndian` or `:BigEndian`, byteswapping will occur of the endianness if the host system does not match the endianness of `io`.
