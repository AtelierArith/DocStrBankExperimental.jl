```
Elastic_Collision
```

多群弾性衝突断面積の生成のためのパラメータを定義するために使用される構造体。

# 必須フィールド

  * 該当なし

# オプションフィールド - デフォルト値付き

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Electron,Electron) => ["S"],(Positron,Positron) => ["S"])` : 相互作用プロセスタイプの辞書で、形式は (入射粒子, 出力粒子) => 関連する相互作用タイプのリストであり、値は次のように対応します：

      * `(Electron,Electron) => ["S"]` : 電子の弾性相互作用。
      * `(Positron,Positron) => ["S"]` : 陽電子の弾性相互作用。
