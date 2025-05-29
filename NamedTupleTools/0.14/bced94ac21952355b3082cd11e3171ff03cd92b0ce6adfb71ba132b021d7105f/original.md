```
namedtuple(  name1, name2, ..  )
namedtuple( (name1, name2, ..) )
namedtuple(  namedtuple )
```

Generate a NamedTuple prototype by specifying or obtaining the fieldnames. The prototype is applied to fieldvalues, giving a completed NamedTuple.

# Example

julia> ntprototype = namedtuple( :a, :b, :c )

NamedTuple{(:a, :b, :c),T} where T<:Tuple

julia> nt123 = ntprototype(1, 2, 3)

(a = 1, b = 2, c = 3)

julia> ntAb3 = ntprototype("A", "b", 3)

(a = "A", b = "b", c = 3)

see: [`isprototype`](@ref)
