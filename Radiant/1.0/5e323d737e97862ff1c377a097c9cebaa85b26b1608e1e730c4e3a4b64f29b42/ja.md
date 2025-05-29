```
光電効果
```

多群光電交差断面の生成のためのパラメータを定義するために使用される構造体。

# 必須フィールド

  * 該当なし

# オプションフィールド - デフォルト値付き

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Photon,Photon) => ["A"],(Photon,Electron) => ["P"])` : 相互作用プロセスのタイプの辞書で、形式は (入射粒子, 出力粒子) => 関連する相互作用タイプのリストであり、値は次のように対応します：

      * `(Photon,Photon) => ["A"]` : 入射光子の吸収。
      * `(Photon,Electron) => ["P"]` : 生成された光電子。
