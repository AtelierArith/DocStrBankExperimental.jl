```
Index(dim::Int; tags::Union{AbstractString, TagSet} = "",
                plev::Int = 0)
```

Create an `Index` with a unique `id`, a TagSet given by `tags`, and a prime level `plev`.

# Examples

```jldoctest; filter=r"id=[0-9]{1,3}"
julia> i = Index(2; tags = "l", plev = 1)
(dim=2|id=818|"l")'

julia> dim(i)
2

julia> plev(i)
1

julia> tags(i)
"l"
```
