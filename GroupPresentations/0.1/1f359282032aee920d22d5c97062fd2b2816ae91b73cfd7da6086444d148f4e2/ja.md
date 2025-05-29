`AbsWord(word, generators)`

与えられた生成元 `gens` を使用して、Tietze 単語 `word` を絶対単語に変換します。

```julia-repl
julia> AbsWord([-1,-2,1,-3,-3],AbsWord.([:a,:b,:c]))
a⁻¹b⁻¹ac⁻²
```
