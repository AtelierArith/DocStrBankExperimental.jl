```
get_strongly_connected_components(h::H) where {H <: AbstractDirectedHypergraph}
```

有向ハイパーグラフ `h` の強連結成分の配列を返します（頂点のベクトルの配列）。これは、Francisco José Martín-Recuerda Moyano の「ナイーブ」アルゴリズムに基づいています（博士論文、2016年）。
