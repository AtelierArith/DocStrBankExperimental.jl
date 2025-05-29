```
Compton
```

多群コンプトン断面積の生成のためのパラメータを定義するために使用される構造。

# 必須フィールド

  * 該当なし

# オプションフィールド - デフォルト値付き

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Photon,Photon) => ["S"],(Photon,Electron) => ["P"])` : 相互作用プロセスのタイプの辞書で、形式は (入射粒子, 出力粒子) => 関連する相互作用タイプのリストであり、値は次のように対応します：

      * `(Photon,Photon) => ["S"]` : コンプトン相互作用に従った入射光子の散乱。
      * `(Photon,Electron) => ["P"]` : コンプトン相互作用に従って生成された電子。
