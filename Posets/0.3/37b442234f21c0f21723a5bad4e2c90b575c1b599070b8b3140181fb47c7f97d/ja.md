```
comparability_graph(p::Poset)
```

`p`の比較可能性グラフを返します。これは、`p[i] < p[j]` または `p[j] < p[i]` の場合に限り、`i` と `j` の間にエッジがあるグラフです。
