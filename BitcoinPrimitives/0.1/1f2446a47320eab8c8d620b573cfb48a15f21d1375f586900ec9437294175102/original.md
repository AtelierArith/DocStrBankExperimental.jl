```
target(header::Header) -> BigInt
```

Returns the proof-of-work target based on the bits

```
last byte is exponent
the first three bytes are the coefficient in little endian
the formula is: coefficient * 256**(exponent-3)
```
