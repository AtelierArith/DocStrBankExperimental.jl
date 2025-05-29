```
nlevels(nlev, tag='S')
```

`tag`の前に`1:nlev`をゼロで左パディングした`Vector{String}`を返します。

# 例

```julia-repl
julia> show(nlevels(10))
["S01", "S02", "S03", "S04", "S05", "S06", "S07", "S08", "S09", "S10"]
```
