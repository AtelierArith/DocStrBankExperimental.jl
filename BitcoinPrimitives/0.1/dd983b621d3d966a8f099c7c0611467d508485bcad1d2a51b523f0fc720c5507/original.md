```
script(::Vector{UInt8}; type::Symbol=:P2WSH) -> Script
```

Returns a `Script` of set type for given hash.

  * `type` can be `:P2PKH`, `:P2SH`, `:P2WPKH` or `:P2WSH`
  * hash must be 32 bytes long for P2WSH script, 20 for the others
