An  `AbsWord` represents an  element of the  free group on some generators. The  generators  are  indexed  by  `Symbols`.  For  example  the  `Absword` representing `a³b⁻²a` is represented internally as `[:a => 3, :b => -2, :a => 1]`. The mulitiplcation follows the group rule:

```julia-repl
julia> w=AbsWord([:a => 3, :b => -2, :a => 1])
a³b⁻²a

julia> w*AbsWord([:a=>-1,:b=>1])
a³b⁻¹

```

A positive `AbsWord` may be obtained by giving `Symbols` as arguments

```julia-repl
julia> AbsWord(:b,:a,:a,:b)
ba²b
```
