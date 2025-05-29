```
Pair_Production
```

多群ペア生成断面積の生成のためのパラメータを定義するために使用される構造。

# 必須フィールド

  * 該当なし

# オプションフィールド - デフォルト値付き

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Photon,Photon) => ["A"],(Photon,Electron) => ["P"],(Photon,Positron) => ["P"])` : 相互作用プロセスのタイプの辞書で、形式は (入射粒子, 出力粒子) => 関連する相互作用タイプのリストであり、値は次のように対応します：

      * `(Photon,Photon) => ["A"]` : 入射光子の吸収。
      * `(Photon,Electron) => ["P"]` : 生成された電子。
      * `(Photon,Positron) => ["P"]` : 生成された陽電子。
  * `angular_scattering_type::String=modified_dipole` : 角散乱のタイプで、次の値を取ることができます：

      * `angular_scattering_type = modified_dipole` : Poskus (2019) の形状関数に基づく修正された双極子分布。
      * `angular_scattering_type = sommerfield` : Sommerfield分布。
