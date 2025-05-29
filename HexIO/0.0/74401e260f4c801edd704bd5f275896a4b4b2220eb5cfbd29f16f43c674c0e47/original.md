```
pack(io::IO, source, endianness::Symbol = :NativeEndian)
```

Given an input `source`, pack it into `io`, byte-swapping according to the given `endianness` of `io`. If `endianness` is `:NativeEndian` (the default), no byteswapping will occur.  If `endianness` is `:LittleEndian` or `:BigEndian`, byteswapping will occur if the endianness of the host system does not match the endianness of `io`.
