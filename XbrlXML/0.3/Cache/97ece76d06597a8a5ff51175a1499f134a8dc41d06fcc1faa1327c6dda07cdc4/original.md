```
headers(cache::HttpCache)::Dict
```

Return the headers of a cache.

# Example

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/");

julia> header!(cache, "User-Agent" => "You youremail@domain.com");

julia> headers(cache)
Dict{String, String} with 1 entry:
  "User-Agent" => "You youremail@domain.com"
```
