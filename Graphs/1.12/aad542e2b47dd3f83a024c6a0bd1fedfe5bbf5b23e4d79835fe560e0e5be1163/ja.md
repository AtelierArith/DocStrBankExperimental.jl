```
transitiveclosure(g, selflooped=false)
```

有向グラフの推移閉包をDFSを使用して計算します。推移閉包を表すグラフを返します。`selflooped`が`true`の場合、グラフに自己ループを追加します。

### パフォーマンス

時間計算量は$\mathcal{O}(|E||V|)$です。

# 例

```jldoctest
julia> using Graphs

julia> barbell = blockdiag(complete_digraph(3), complete_digraph(3));

julia> add_edge!(barbell, 1, 4);

julia> ne(barbell)
13

julia> ne(transitiveclosure(barbell))
21
```
