```
steiner_tree(g, term_vert, distmx=weights(g))
```

接続された無向グラフ `g` のおおよその最小シュタイナー木を、`distmx` で表される正のエッジ重みを使用して返します。[近似シュタイナー木](https://en.wikipedia.org/wiki/Steiner_tree_problem#Approximating_the_Steiner_tree)を使用します。最小シュタイナー木問題は、`g` の中で最小の重みを持つエッジの部分集合を見つけることを含み、すべての頂点が `term_vert` に接続される必要があります。

`t = length(term_vert)`。

### パフォーマンス

実行時間: O(t*(t*log(t)+|E|*log(|V| )) メモリ: O(t*|V|) 近似係数: 2-2/t
