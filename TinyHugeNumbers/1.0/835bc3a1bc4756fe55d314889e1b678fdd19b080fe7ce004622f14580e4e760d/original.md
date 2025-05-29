```
tiny
```

`tiny` represents a (wow!) tiny number that can be used in a various computations without unnecessary type promotions.

`tiny` is defined as:

  * `1.0f-6` for `Float32`
  * `1e-12` for `Float64`
  * `big"1e-24"` for `BigFloat`
  * `10 * eps(F)` for an arbitrary type `F <: AbstractFloat`

# Example

```jldoctest
julia> tiny
tiny

julia> 1 + tiny
1.000000000001

julia> tiny + 1
1.000000000001

julia> 1f0 + tiny
1.000001f0

julia> big"1.0" + tiny
1.000000000000000000000001

julia> big"1" + tiny
1.000000000000000000000001
```

See also: [`huge`](@ref)
