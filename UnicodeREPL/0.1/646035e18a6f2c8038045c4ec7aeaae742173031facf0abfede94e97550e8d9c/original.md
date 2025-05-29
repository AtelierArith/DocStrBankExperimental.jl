```
ufind(r::Union{AbstractString,Regex})
```

Return the Unicode completion pairs whose keys match `r`

## Example

```julia-repl
julia> using UnicodeREPL
REPL mode unicode_repl initialized. Press ^ to enter and backspace to exit.

julia> ufind("feed")
2-element Vector{Pair{String, String}}:
 "\\:breast-feeding:" => "🤱"
         "\\linefeed" => "↴"

julia> ufind(r"^[^:]*feed")
1-element Vector{Pair{String, String}}:
 "\\linefeed" => "↴"

julia>
```

Note that Unicode codepages themselves are not included, so the mapping `"\\u(feed)" => "ﻭ"` is not in the output.
