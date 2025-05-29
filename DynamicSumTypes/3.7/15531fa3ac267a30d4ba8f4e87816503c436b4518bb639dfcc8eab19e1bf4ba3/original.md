```
allvariants(SumType)
```

Returns all the enclosed variants types in the sum type in a namedtuple.

## Example

```julia
julia> using DynamicSumTypes

julia> struct A x::Int end;

julia> struct B end;

julia> @sumtype AB(A, B)

julia> allvariants(AB)
(A = A, B = B)
```
