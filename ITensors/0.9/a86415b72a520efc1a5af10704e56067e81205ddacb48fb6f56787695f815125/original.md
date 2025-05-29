```
hastags(i::Index, ts::Union{AbstractString,TagSet})
```

Check if an `Index` `i` has the provided tags, which can be a string of comma-separated tags or a TagSet object.

# Examples

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2, "SpinHalf,Site,n=3")
(dim=2|id=861|"Site,SpinHalf,n=3")

julia> hastags(i, "SpinHalf,Site")
true

julia> hastags(i, "Link")
false
```
