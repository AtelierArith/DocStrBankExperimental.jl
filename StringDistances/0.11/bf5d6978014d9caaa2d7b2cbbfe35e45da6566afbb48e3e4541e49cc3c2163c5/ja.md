```
compare(s1, s2, dist)
```

文字列 `s1` と `s2` の間の類似度スコアを、距離 `dist` に基づいて 0 から 1 の範囲で返します。

### 例

```julia-repl
julia> compare("martha", "marhta", Levenshtein())
0.6666666666666667
```
