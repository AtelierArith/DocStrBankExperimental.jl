```
octet(g::ECGroup; mode = :uncompressed|:hybrid|:compressed)::Vector{UInt8}
```

Converts elliptic curve point to an octet representation as specified in FIPS 186-4 standart. The `mode=:uncompressed|:hybrid|:compressed` can be used to specify compression mode. 

See also `iscompressable`
