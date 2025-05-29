`rename_variables(p,v)` renames `variables(p)` to `v`

`rename_variables(p,l::Pair{Symbol,Symbol}...)` renames the  variables in `p` as indicated by the pairs in `l`.

```julia-repl
julia> @Mvp x,y,z; p=x+y+z
Mvp{Int64}: x+y+z

julia> rename_variables(p,Symbol.('A':'Z'))
Mvp{Int64}: A+B+C

julia> rename_variables(p,[:U,:V])
Mvp{Int64}: U+V+z

julia> rename_variables(p,:x=>:U,:z=>:V) # faster than p(;x=Mvp(:U),z=Mvp(:V))
Mvp{Int64}: U+V+y
```
