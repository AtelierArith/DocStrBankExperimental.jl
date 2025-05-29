`rename_variables(p,v)` は `variables(p)` を `v` に名前変更します。

`rename_variables(p,l::Pair{Symbol,Symbol}...)` は `l` のペアに従って `p` の変数の名前を変更します。

```julia-repl
julia> @Mvp x,y,z; p=x+y+z
Mvp{Int64}: x+y+z

julia> rename_variables(p,Symbol.('A':'Z'))
Mvp{Int64}: A+B+C

julia> rename_variables(p,[:U,:V])
Mvp{Int64}: U+V+z

julia> rename_variables(p,:x=>:U,:z=>:V) # p(;x=Mvp(:U),z=Mvp(:V) よりも速い
Mvp{Int64}: U+V+y
```
