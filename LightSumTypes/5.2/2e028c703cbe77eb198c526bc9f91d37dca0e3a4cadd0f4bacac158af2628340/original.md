```
@sumtype SumTypeName(Types) [<: AbstractType]
```

Creates a sumtype composed by the given types. It optionally accept also an abstract supertype.

## Example

```julia
julia> using LightSumTypes

julia> struct A x::Int end;

julia> struct B end;

julia> @sumtype AB(A, B)
```
