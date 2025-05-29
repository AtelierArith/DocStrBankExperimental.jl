```
struct GreedyClique
    vertices::BitArray
    mutuals::BitArray
end
```

# 引数

  * `vertices::BitArray`: クリークを定義する部分グラフの頂点。フルグラフの頂点数にわたるBitVectorで、クリークのメンバーとして識別される場合はtrue、そうでない場合はfalseです。
  * `mutuals::BitArray`: クリークに隣接する頂点（潜在的なクリークメンバー）
