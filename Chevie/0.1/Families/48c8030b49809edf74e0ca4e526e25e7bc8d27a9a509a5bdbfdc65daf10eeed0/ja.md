`ndrinfeld_double(g)`

この関数は、群 `g` の Drinfeld ダブルに関連するファミリーが持つ要素の数を計算せずに返します。明らかな利点は速度です。

```julia-repl
julia> Families.ndrinfeld_double(complex_reflection_group(5))
378
```
