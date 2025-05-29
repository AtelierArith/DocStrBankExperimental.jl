```
noise(n, noise::AbstractNoise)
```

Compute noise function `noise` at position `n`.

## Examples

```jldoctest
julia> sqn = SquirrelNoise5()
SquirrelNoise5(0x00000000)

julia> noise(5, sqn)
0x933e65af
```
