```
fletcher_checksum(T, data, init::T = zero(T), modulo::T = typemax(T), blocksize::Integer = 1)
```

Compute a hash of `data` using Fletcher's checksum.

Fletcher's checksum computes two values: `c0`, a running sum of values modulo some number, and `c1`, a running sum of `c0` values modulo some number. The two values are contatenated bitwise into a single unsigned integer.

This function is fast and good at detecting small errors. Flaws to keep in mind are:

1. zero values at the beginning of `data` do not affect the checksum value at all (unless the initial value is set to something other than zero); and
2. the worst-case performance for this algorithm occurs when data are truly random, but all errors of up to 2 bits are detected on all runs of data of length `modulo * (sizeof(T)*4)` bits.

## Arguments

  * `T`: An unsinged integer type.
  * `data`: A single `Unsigned` value or an iterator of values.
  * `init::Unsigned = zero(T)`: Optional starting value.
  * `modulo::T = typemax(T)`: Optional modulo value, applied independently to the sum and the sum-of-sums after each block is summed.
  * `blocksize::Integer = 1`: Optional block size for summing before applying the modulo operation. `blocksize` should be chosen with `modulo`, `T`, and `eltype(data)` in mind to make sure the sum operation does not overflow.

Predefined convenience functions are `fletcher16`, `fletcher32`, and `fletcher64` for the standard modulo value of `typemax(T)` shifted right half the number of bits in the checksum, and `fletcher16a`, `fletcher32a`, and `fletcher64a` for the alternate modulo value of `1` left shifted half the number of bits in the checksum.

See also: [adler32](@ref).
