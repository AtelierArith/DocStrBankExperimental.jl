```
weights(g::AbstractValGraph[, key]; zerovalue)
```

エントリ (i,j) が `g` の特定の `key` に対するエッジ `i -- j` の値である行列を返します。

`g` にエッジ値がない場合、`key` は省略され、`DefaultDistance(g)` が返されます。そうでなければ、結果は `ValMatrix` です。`g` にエッジごとに単一の値がある場合、`key` は省略できます。オプション引数 `zerovalue` が指定されている場合、エントリ (i, j) が `g` のエッジでない場合にこの値が使用されます。`zerovalue` はエッジ値がないグラフには使用できません。
