```
cachedir(cache::HttpCache)::String
```

Return the local directory of a cache.

# Example

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/");

julia> cachedir(cache)
"/Users/user/cache/"
```
