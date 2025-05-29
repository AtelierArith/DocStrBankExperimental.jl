```
variable_symbols(indp, [i])
```

インデックスプロバイダー `indp` で解決されるシンボリック変数のベクトルを返します。`constant_structure(sys) == false` の場合、現在の時間インデックスを示す追加のパラメータを受け入れます。返されるベクトルは変更されるべきではありません。

このインターフェースを使用してシンボリックインデックスで `Base.getindex` を実装するタイプの場合、短縮形 `valp[solvedvariables]` は `valp[variable_symbols(sys)]` の短縮形として使用できます。参照: [`solvedvariables`](@ref).
