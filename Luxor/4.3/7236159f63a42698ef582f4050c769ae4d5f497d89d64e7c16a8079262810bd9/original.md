```
@savesvg begin
    body
end w h
```

Like `@drawsvg` but returns the raw SVG code of the drawing in a string. Uses `svgstring`.

Unlike `@draw` (PNG), there is no background, by default.

This example scans the generated SVG for color values:

```julia-repl
julia> s = @savesvg begin
           julialogo()
       end

julia> eachmatch(r"rgb.*?;", s) |> collect
5-element Vector{RegexMatch}:
 RegexMatch("rgb(0%,0%,0%);")
 RegexMatch("rgb(25.1%,38.8%,84.7%);")
 RegexMatch("rgb(22%,59.6%,14.9%);")
 RegexMatch("rgb(58.4%,34.5%,69.8%);")
 RegexMatch("rgb(79.6%,23.5%,20%);")
```
