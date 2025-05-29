```
@sumtype SumTypeName(Types) [<: AbstractType]
```

The macro creates a sumtypes composed by the given types. It optionally accept also an abstract supertype.

## Example

```julia
julia> using DynamicSumTypes

julia> struct A x::Int end;

julia> struct B end;

julia> @sumtype AB(A, B)
```
