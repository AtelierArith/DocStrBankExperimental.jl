```
clean_team_abbrs(team::AbstractString; current_location::Bool = true, keep_non_matches::Bool = true)
```

チームの略称をNFLverseに適した略称にクリーンアップします。

# 例

```julia-repl
julia> clean_team_abbrs("SD")
"LAC"
```
