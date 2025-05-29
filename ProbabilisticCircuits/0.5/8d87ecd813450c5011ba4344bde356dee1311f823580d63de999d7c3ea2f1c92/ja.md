```
random_region_graph(X::AbstractVector, depth::Int = 5, replicas::Int = 2, num_splits::Int = 2)
```

  * `X`: 含めるすべての変数のベクター; ルート領域用
  * `depth`: 分割の層数
  * `replicas`: 複製またはパーティションの数（複製はルート領域のみに使用; 他の領域では1つのパーティション（内部ノード）または葉のために0パーティションのみ）
  * `num_splits`: 各パーティションの分割数; 変数をランダムに同じサイズの領域に分割
