```
skeleton(n::Integer, I) -> g, S
skeleton(g, I) -> g, S
```

`I`を使用して`1:n`変数の集合に対して無向PCスケルトンアルゴリズムを実行します。`g`の部分グラフまたは`n`頂点の完全無向グラフから始めます。スケルトングラフと分離集合を返します。
