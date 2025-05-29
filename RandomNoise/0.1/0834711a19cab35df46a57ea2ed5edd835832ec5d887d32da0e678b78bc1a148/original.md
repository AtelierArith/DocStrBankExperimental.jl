```
SquirrelNoise5x2 <: AbstractNoise{UInt64}
```

A 64 bits noise function made by stacking two `SquirrelNoise5()` together.

## Fields

  * `seed1::UInt32 = 0` the first seed
  * `seed2::UInt32 = 1` the second seed

When constructing an instance with both seeds equal, a `DomainError` will be raised.

## Examples

```jldoctest
julia> sqnx2 = SquirrelNoise5x2()
SquirrelNoise5x2(0x00000000, 0x00000001)

julia> noise(0, sqnx2)
0xd40e6352d9ba8dce

julia> noise(1, sqnx2)
0x0f9b5434d68ee534
```
