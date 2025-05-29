```
StrF{S}(::String)
```

A string of less than `S` bytes, represented using 0-terminated UTF-8.

# Internal representation

`bytes` are stored as an `SVector{S, UInt8}`, where `S` is the maximum number of bytes. They are not validated to be conforming UTF-8. A terminating `0x00` follows **if and only if** the string is shorter than `S` bytes.

This follows the `str#` ("sturfs") representation of [Stata](https://www.stata.com/help.cgi?dta).

# Operations

A comparisons, conversion, and a few operations are supported, but this is primarily meant as a storage type. For complex manipulations, it is recommended that you convert to `String`.
