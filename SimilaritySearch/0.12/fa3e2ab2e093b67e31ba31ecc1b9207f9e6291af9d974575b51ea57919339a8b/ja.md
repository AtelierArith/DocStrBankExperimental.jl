```
struct SearchResult
    res::KnnResult  # 結果構造体
    cost::Int32  # 距離の数 (アルゴリズムが許可する場合)
    eblocks::Int32 # 評価されたブロックの数 (インデックスにとって何を意味するかは不明)
end
```

典型的な検索 knn クエリの応答
