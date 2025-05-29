```
untokenise!(txt::Txt, W::Union{AbstractCharSpace, Nothing} = nothing; kwargs)
```

Unokenises `txt` in place, updating the `raw::String` field and `is_tokenised` and clearing `tokenised`

# Examples

```julia-repl
julia> t
12-token Txt:
[13, 18, 23, 15, 15, 4, 13, 15, 13, 5, 14, 20]

julia> untokenise!(t)
14-character Txt:
"Mr Wood moment"
```
