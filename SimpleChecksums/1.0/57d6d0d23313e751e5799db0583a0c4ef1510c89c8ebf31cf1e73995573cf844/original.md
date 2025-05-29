```
adler32(data, init::Unsigned = one(UInt32))
```

Compute Adler's 32-bit checksum.

Adler's 32-bit checksum is the same as Fletcher's 32-bit checksum with a modulus of 65521 (the largest 16-bit prime) and an inital value of one. This is a strict improvement on `fletcher16`, but has a higher probability of collision, worse likelihood of error detection, and is slower than `fletcher32`. Prefer `fletcher32` instead.
