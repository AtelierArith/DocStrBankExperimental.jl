```
sysv_checksum(UInt16, data, init::UInt16 = zero(UInt16))
```

Compute a hash of `data` using the method defined in SYS-V's sum utility (and implemented in the GNU sum program).

The SYS-V checksum computes a 16-bit checksum value using a simple 32-bit additive sum, then folding the sum into a 16-bit number by adding the low 16 bits to the high 16 bits (shifted right by 16 bits). This fold is performed twice to guarantee the result is a 16-bit number. Unlike the SYS-V and GNU implementations, the sum in this implementation is allowed to overflow, which resets the sum to zero (SYS-V and GNU will raise an error instead).

This function is very fast but suffers from many collisions. Flaws to keep in mind are:

1. zero values anywhere in `data` do not affect the checksum value at all (unless the initial value is set to something other than zero); and
2. the order of the data can be permuted without affecting the checksum value.

## Arguments

  * `data`: A single `Unsigned` value or an iterator of values.
  * `init::UInt16 = zero(UInt16)`: Optional starting value.

Predefined convenience function is `sysv16`.

See also: [`additive16`](@ref).
