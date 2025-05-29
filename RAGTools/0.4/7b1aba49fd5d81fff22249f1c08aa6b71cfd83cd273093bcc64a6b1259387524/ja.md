```
CandidateChunks
```

指定されたインデックス（`index_id`で識別）内のチャンクへの参照を格納するための構造体で、`positions`と`scores`が含まれ、類似性の強さを保持します（=1が最高、最も類似）。これはRAGの取得段階の結果です。

# フィールド

  * `index_id::Symbol`: 候補が引き出されるインデックスのID
  * `positions::Vector{Int}`: インデックス内の候補の位置（つまり、`5`

```
はインデックス内の5番目のチャンクを指します - `chunks(index)[5]`)
```

  * `scores::Vector{Float32}`: クエリからの候補の類似性スコア（高いほど良い）
