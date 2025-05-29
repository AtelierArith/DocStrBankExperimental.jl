```
SquirrelNoise5
```

The SquirrelNoise5 32 bits random noise function, originally by Squirrel Eiserloh.

See http://eiserloh.net/noise/SquirrelNoise5.hpp for the original C++ code.

## Fields

  * `seed::UInt32 = 0` seed of the noise function.

## Examples

```jldoctest
julia> noise(0,SquirrelNoise5())
0x16791e00

julia> noise(1,SquirrelNoise5())
0xc895cb1d

julia> noise(0,SquirrelNoise5(32))
0x9ef5c661
```
