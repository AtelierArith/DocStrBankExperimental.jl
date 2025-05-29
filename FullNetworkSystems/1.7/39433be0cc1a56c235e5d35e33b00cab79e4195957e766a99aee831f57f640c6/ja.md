```
compute_lodf(system, branch_names_out) -> KeyedArray
compute_lodf(system::System, ptdf_matrix, branch_names_out) -> KeyedArray
compute_lodf(buses, branches, ptdf, branch_names_out) -> KeyedArray
```

ネットワークの `M*O` DCライン障害分配係数 (DC-LODF) 行列を返します。

**重要な注意:** 現在の実装では、緊急事態シナリオにサービス中のラインがない場合にのみ `lodf` を使用します。この関数は、サービス中のラインを無視したい場合にも使用できます。

# 入力

  * `buses::Buses`
  * `branches::Branches`
  * `ptdf_matrix`: システムの事前計算されたPTDF行列
  * `branch_names_out`: 緊急事態シナリオで出て行くブランチの名前。

# 出力

  * `KeyedArray` としてのLODF行列。軸はブランチ名と `branch_names_out` です。

!!! note
    結果のLODF行列は入力PTDF行列に敏感です。しきい値を設定したPTDFを入力として使用すると、完全なPTDFを使用するのに比べて不正確になる可能性があります。

