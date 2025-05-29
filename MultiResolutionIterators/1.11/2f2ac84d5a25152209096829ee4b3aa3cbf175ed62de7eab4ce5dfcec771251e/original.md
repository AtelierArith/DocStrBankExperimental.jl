```
consolidate(xs)
```

This is the generalisation of collect. The convention is that `collect(::T)::Vector{eltype{T}}`. `consolidate` has a weaker convention, it is that it should return some type that has working `getindex`. To be precise it is that  for `consolidate(::T)::V` we have `eltype(V)==eltype(T)`, and `∀i`, `getindex(collect(xs), ii) == getindex(consolidate(xs), ii)`

For most types it defaults to `collect` For various series of `Char`s it converts them to strings

You can overload it if you want to change its behavour. In particular if there is cheap way of making an indexable copy of your type. (eg if your type is immutable)

For example:

```julia
struct MyType # Bad type but what ever
    content
    field
end
MultiResolutionIterators.consolidate(xs::MyType) == MyType(consolidate(xs.content), xs.field)
```

It is useful if there are other fields in your type that you want to preserve,
