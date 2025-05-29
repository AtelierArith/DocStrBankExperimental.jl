```
Fourier{T<:Real} <: BaseSpace
```

Fourier sequence space whose elements are Fourier sequences of a prescribed order and frequency.

Fields:

  * `order :: Int`
  * `frequency :: T`

Constructor:

  * `Fourier(::Int, ::Real)`

See also: [`Taylor`](@ref) and [`Chebyshev`](@ref).

# Examples

```jldoctest
julia> s = Fourier(2, 1.0)
Fourier(2, 1.0)

julia> order(s)
2

julia> frequency(s)
1.0
```
