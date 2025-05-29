```
indent(str::AbstractString, n::Int)
```

各非空行を `n` スペースでインデントします。

# 例

```jldoctest; setup = :(using MultilineStrings)
julia> indent("a\nb", 4)
"    a\n    b"

julia> indent("  a\n  \n  b", 2)
"    a\n  \n    b"
```

`Base.unindent` と `Base.indentation` も参照してください。
