```
NoiseRNG{N,T} <: AbstractRNG where {N,T<:AbstractNoise{N}}
```

Wrapper type to use a noise function as a rng for use in `rand()`.

## Fields

  * `noise::T` : the noise function.
  * `counter::N = zero(N)` : a counter indicating where the sequence of generated numbers is currently at.

## Examples

```jldoctest julia> rng = NoiseRNG(SquirrelNoise5()) NoiseRNG{UInt32, SquirrelNoise5}(SquirrelNoise5(0x00000000), 0x00000000)

julia> rand(rng) 0.08778560161590576 ````
