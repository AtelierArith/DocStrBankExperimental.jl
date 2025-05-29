```
hasext(path, ext::String) -> Bool
hasext(path, exty::Symbol) -> Bool
```

Checks a path's extension. A string must match the extension exactly:

```julia
julia> hasext("myfile.txt", "txt")
true

julia> hasext("myfile.TXT", "txt")
false
```

A symbol matches in an extension group, and is also case-insensitive:

```julia
julia> hasext("myfile.jpeg", :jpeg)
true

julia> hasext("myfile.jpg", :jpeg)
true

julia> hasext("myfile.JPEG", :jpeg)
true

julia> hasext("myfile.jpeg", :jpg)  # any extension in an extension group works as a symbol for that group
true
```

See also `exty`.
