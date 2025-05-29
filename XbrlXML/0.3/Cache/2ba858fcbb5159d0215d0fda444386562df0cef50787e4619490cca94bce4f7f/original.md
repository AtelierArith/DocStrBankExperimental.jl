```
header!(cache::HttpCache, header::Pair)::Dict
```

Add a header pair to a cache and return the headers.

# Example

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/");

julia> header!(cache, "User-Agent" => "You youremail@domain.com")
Dict{String, String} with 1 entry:
  "User-Agent" => "You youremail@domain.com"
```
