`reflection_character(W::ComplexReflectionGroup)` または `reflchar`

`W` の反射キャラクターを返します。`W` が不可約である場合、これは `CharTable(W).irr[charinfo(W).extRefl[2]]` です。

```julia-repl
julia> reflchar(coxgroup(:A,3))
5-element Vector{Int64}:
  3
  1
 -1
  0
 -1
```
