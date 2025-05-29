```
Taylor <: BaseSpace
```

Taylor sequence space whose elements are Taylor sequences of a prescribed order.

Field:

  * `order :: Int`

Constructor:

  * `Taylor(::Int)`

See also: [`Fourier`](@ref) and [`Chebyshev`](@ref).

# Examples

```jldoctest
julia> s = Taylor(2)
Taylor(2)

julia> order(s)
2
```
