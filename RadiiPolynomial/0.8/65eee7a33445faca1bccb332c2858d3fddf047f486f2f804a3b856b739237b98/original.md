```
Chebyshev <: BaseSpace
```

Chebyshev sequence space whose elements are Chebyshev sequences of a prescribed order.

Field:

  * `order :: Int`

Constructor:

  * `Chebyshev(::Int)`

See also: [`Taylor`](@ref) and [`Fourier`](@ref).

# Examples

```jldoctest
julia> s = Chebyshev(2)
Chebyshev(2)

julia> order(s)
2
```
