```
replacetags(i::Index, tsold, tsnew)

replacetags(i::Index, tsold => tsnew)
```

If the tag set of `i` contains the tags specified by `tsold`, replaces these with the tags specified by `tsnew`, preserving any other tags. The arguments `tsold` and `tsnew` can be comma-separated strings of tags, or TagSet objects.

# Examples

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2; tags="l,x", plev=1)
(dim=2|id=83|"l,x")'

julia> replacetags(i, "l", "m")
(dim=2|id=83|"m,x")'

julia> replacetags(i, "l" => "m")
(dim=2|id=83|"m,x")'
```
