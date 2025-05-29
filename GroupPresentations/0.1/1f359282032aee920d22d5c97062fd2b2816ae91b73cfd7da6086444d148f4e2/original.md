`AbsWord(word, generators)`

Tranforms Tietze word `word` to an absword, using given generators `gens`.

```julia-repl
julia> AbsWord([-1,-2,1,-3,-3],AbsWord.([:a,:b,:c]))
a⁻¹b⁻¹ac⁻²
```
