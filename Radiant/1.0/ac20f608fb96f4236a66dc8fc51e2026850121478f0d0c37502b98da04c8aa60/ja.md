```
ブレムストラールング
```

多群ブレムストラールング断面積の生成のためのパラメータを定義するために使用される構造体。

# 必須フィールド

  * 該当なし

# オプションフィールド - デフォルト値付き

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Electron,Electron) => ["S"],(Electron,Photon) => ["P"],(Positron,Positron) => ["S"],(Positron,Photon) => ["P"])` : 相互作用プロセスタイプの辞書で、形式は (入射粒子, 出力粒子) => 関連する相互作用タイプのリストであり、値は次のように対応します：

      * `(Electron,Electron) => ["S"]` : ブレムストラールング相互作用に従う入射電子の散乱。
      * `(Electron,Photon) => ["P"]` : 入射電子によるブレムストラールング相互作用に続いて生成された光子。
      * `(Positron,Positron) => ["S"]` : ブレムストラールング相互作用に従う入射陽電子の散乱。
      * `(Positron,Photon) => ["P"]` : 入射陽電子によるブレムストラールング相互作用に続いて生成された光子。
  * `angular_scattering_type::String=modified_dipole` : 角散乱のタイプで、次の値を取ることができます：

      * `angular_scattering_type = modified_dipole` : Poskus (2019) の形状関数に基づく修正された双極子分布。
      * `angular_scattering_type = sommerfield` : ソマー・フィールド分布。
