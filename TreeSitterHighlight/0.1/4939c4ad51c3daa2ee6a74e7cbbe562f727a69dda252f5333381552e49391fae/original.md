```
HighlightBuffer(names_attributes::Dict{String,String})
```

An HighlightBuffer is the object needed to perform syntax highlighting. The names parameter represent the capture groups that should be wrapped in spans. The attributes element corresponds to the corresponding HTML attributes that should be inserted in the span of each of this spans.

```julia
julia> highlighter = Highlighter(Dict(
           "keyword" => "class=keyword",
       ))
Highlighter(Language[])
```
