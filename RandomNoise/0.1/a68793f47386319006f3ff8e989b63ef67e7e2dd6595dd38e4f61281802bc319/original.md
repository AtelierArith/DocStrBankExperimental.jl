```
Murmur3Noise
```

A 32-bit noise function based on the Murmur3 hash function.

## Fields

  * `seed::UInt32 = 0`

## Examples

```jldoctest
julia> m3n = Murmur3Noise()
Murmur3Noise(0x00000000)

julia> noise(0, m3n)
0x2362f9de

julia> noise(1, m3n)
0xfbf1402a
```

```jldoctest
julia> m3n = Murmur3Noise(42)
Murmur3Noise(0x0000002a)

julia> noise(0, m3n)
0x379fae8f

julia> noise(1, m3n)
0xdea578e3
```
