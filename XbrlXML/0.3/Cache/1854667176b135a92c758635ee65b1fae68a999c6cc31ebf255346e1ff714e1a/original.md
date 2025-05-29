```
HttpCache(cache_dir="./cache/", headers=Dict())
```

Create a cache to store files locally for reuse.

`headers` are passed to http `Downloads.download`. Services such as SEC require you to disclose information about your application.

# Example

```jldoctest
julia> using XbrlXML

julia> cache = HttpCache("/Users/user/cache/")
/Users/user/cache/
```
