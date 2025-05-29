```
a_star_algorithm(g::AbstractGraph{U},  
                s::Integer,                       
                t::Integer,                       
                distmx::AbstractMatrix{T}=Graphs.weights(g),
                heuristic::Function = (u,v) -> zero(T)) where {T, U}
```

高レベル関数 - A*探索アルゴリズムの実装: (https://en.wikipedia.org/wiki/A**search*algorithm)。 Graphsライブラリの実装に基づいていますが、パフォーマンスの面で大幅に改善されています。

**引数**

  * `g` : グラフオブジェクト
  * `S` : 開始頂点
  * `t` : 終了頂点
  * `distmx` : 距離行列
  * `heuristic` : 探索ヒューリスティック関数; デフォルトではゼロを返します
