```
Encrypt!(c::Cipher, dst::Array{UInt8, 1}, src::Array{UInt8, 1})
```

Encrypt encrypts the 8-byte buffer src using the key k and stores the result in dst. Note that for amounts of data larger than a block, it is not safe to just call Encrypt on successive blocks.
