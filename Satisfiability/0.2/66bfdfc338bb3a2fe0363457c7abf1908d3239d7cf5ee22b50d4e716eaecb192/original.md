```
nextsize(n::Integer)
```

Returns the smallest unsigned integer type that can store a number with n bits. If n is larger than the largest available type (`UInt128`), returns type `BigInt`.
