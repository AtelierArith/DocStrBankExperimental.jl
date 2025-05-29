```
keeps_filtered(f, types...) -> Bool
```

次の条件が満たされる場合は `true` を返し、そうでない場合は `false` を返します: 関数 `f` が型 `types` の引数で呼び出され、単一の項 `y` を返すとき、`linear_filter(y) == true` が成り立ちます。

デフォルトでは、`keeps_filtered` はすべての引数に対して `false` を返します。これは、不要な（おそらく高価な）`linear_filter` の呼び出しを避けるために変更できます。`f` が項引数で呼び出されたときに線形結合を返す場合、この線形結合に現れるすべての項は、上記の条件を満たします。この場合、`keeps_filtered` の設定は重要ではありません。

詳細は [`LinearCombinations.linear_filter`](@ref) を参照してください。
