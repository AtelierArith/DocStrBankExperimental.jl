```
emptyshim(ContainerType)
emptyshim(ContainerType, ElementType)
```

Create an empty "shim" container that is widen to `ContainerType` when appending elements to it.  Default `ElementType` is `Union{}`.

# Examples

```jldoctest
julia> using MicroCollections, BangBang

julia> @assert append!!(emptyshim(Vector), [0]) == [0]

julia> @assert merge!!(emptyshim(Dict), Dict(:a => 1)) == Dict(:a => 1)

julia> @assert union!!(emptyshim(Set), Set([0])) == Set([0])
```
