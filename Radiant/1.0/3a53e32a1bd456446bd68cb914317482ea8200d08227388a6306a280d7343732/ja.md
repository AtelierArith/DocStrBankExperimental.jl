```
消滅
```

多群消滅断面積の生成のためのパラメータを定義するために使用される構造。

# 必須フィールド

  * 該当なし

# オプションフィールド - デフォルト値付き

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Positron,Positron) => ["A"],(Positron,Photon) => ["P","P_inel","P_brems"],(Photon,Photon) => ["P_pp"])` : 相互作用プロセスタイプの辞書で、形式は (入射粒子, 出力粒子) => 関連する相互作用タイプのリストであり、値は次のように対応します：

      * `(Positron,Positron) => ["A"]` : 入射した陽電子の吸収。
      * `(Positron,Photon) => ["P"]` : 消滅に続く2つの光子の生成。
      * `(Positron,Photon) => ["P_inel"]` : 散乱の下でカットオフエネルギーに従った非弾性衝突陽電子吸収からの消滅光子の生成。
      * `(Positron,Photon) => ["P_brems"]` : 散乱の下でカットオフエネルギーに従ったブレムストラール陽電子吸収からの消滅光子の生成。
      * `(Photon,Photon) => ["P_pp"]` : カットオフエネルギーの下での生成に続く陽電子の吸収からの消滅光子の生成。
