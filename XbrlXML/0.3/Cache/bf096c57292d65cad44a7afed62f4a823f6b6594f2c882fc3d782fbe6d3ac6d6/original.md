```
headers!(cache::HttpCache, header::Vector{Pair})::Dict
```

Add multiple header pairs to a cache and return the headers.

# Example

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/");

julia> newheaders = ["User-Agent" => "You youremail@domain.com", "From" => "You"];

julia> headers!(cache, newheaders)
Dict{String, String} with 2 entries:
  "From"       => "You"
  "User-Agent" => "You youremail@domain.com"
```
