```
to(SomeArray, ::OtherArray)::SomeArray
```

Construct an instance of `SomeArray` from an instance of `OtherArray`.

# Examples

```jldoctest
julia> using AxisArrayConversion: SimpleAxisArray, to

julia> to(SimpleAxisArray, (axes=(a=1:3,), values=[10,20,30]))
SimpleAxisArray(axes = (a = 1:3,), values = [10, 20, 30])

julia> arr = to(SimpleAxisArray, (axes=(a=1:3,), values=[10,20,30]))
SimpleAxisArray(axes = (a = 1:3,), values = [10, 20, 30])

julia> to(NamedTuple, arr)
(axes = (a = 1:3,), values = [10, 20, 30])

julia> to(NamedTuple, [1 2; 3 4])
(axes = (x1 = Base.OneTo(2), x2 = Base.OneTo(2)), values = [1 2; 3 4])
```

This function should not be overloaded. Instead [`namedtuple`](@ref) and [`from_namedtuple`](@ref) should be overloaded.

This function is part of the public API and subject to SemVer guarantees.
