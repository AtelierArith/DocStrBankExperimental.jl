```
variable_index(indp, sym, [i])
```

与えられた変数 `sym` の `indp` におけるインデックスを返します。そうでない場合は `nothing` を返します。[`constant_structure`](@ref) が `false` の場合、現在の時間インデックスを追加のパラメータ `i` として受け入れます。
