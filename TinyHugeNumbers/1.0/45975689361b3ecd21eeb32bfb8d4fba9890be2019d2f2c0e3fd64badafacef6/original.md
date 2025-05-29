```
huge
```

`huge` represents a (wow!) huge number that can be used in a various computations without unnecessary type promotions.

`huge` is defined as:

  * `1.0f+6` for `Float32`
  * `1e+12` for `Float64`
  * `big"1e+24"` for `BigFloat`
  * `inv(tiny(F))` for an arbitrary type `F <: AbstractFloat`

# Example

```jldoctest
julia> huge
huge

julia> 1 + huge
1.000000000001e12

julia> huge + 1
1.000000000001e12

julia> 1f0 + huge
1.000001f6

julia> big"1.0" + huge
1.000000000000000000000001e+24

julia> big"1" + huge
1.000000000000000000000001e+24
```

See also: [`tiny`](@ref)
