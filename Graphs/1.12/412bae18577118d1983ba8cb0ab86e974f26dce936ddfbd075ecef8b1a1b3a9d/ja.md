```
steiner_tree(g, term_vert, distmx=weights(g))
```

正のエッジ重みが `distmx` で表される接続された無向グラフ `g` の近似最小シュタイナー木を返します。最小シュタイナー木問題は、すべての頂点が `term_vert` に接続されるように、`g` の中から最小の重みを持つエッジの部分集合を見つけることを含みます。

`t = length(term_vert)`。

### パフォーマンス

実行時間: O(t*(t*log(t)+|E|*log(|V| )) メモリ: O(t*|V|) 近似係数: 2-2/t
