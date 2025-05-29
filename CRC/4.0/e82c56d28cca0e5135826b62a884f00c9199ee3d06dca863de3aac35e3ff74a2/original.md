```
crc(spec[, tables = Multiple])
```

Create a crc function implementing `spec` with lookup table behaviour `tables`. Available specs are listed in [`ALL`](@ref) and tables can be either [`Multiple`](@ref), [`Single`](@ref) or [`NoTables`](@ref).

The returned function accepts `String`, `Vector{UInt8}` or `IO` and calculates the CRC checksum. An optional boolean parameter `append` can be used for chained application.

A faster CRC32*C* implementation is available in Stdlib: [`CRC32c`](@ref).

# Examples

```julia-repl
using CRC

# create our own crc function, just once
crc32 = crc(CRC_32)

# use the crc function created above, many times
for s in ["hello", "there"]
    println(s => crc32(s))
end
```
