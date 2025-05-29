Inelastic_Collision

多群非弾性衝突断面積の生成のためのパラメータを定義するために使用される構造体。

# 必須フィールド

  * 該当なし

# オプションフィールド - デフォルト値付き

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Positron,Positron) => ["S"],(Positron,Electron) => ["P"],(Electron,Electron) => ["S","P"])` : 相互作用プロセスタイプの辞書で、形式は (入射粒子, 出力粒子) => 関連する相互作用タイプのリストであり、値は次のように対応します：

      * `(Positron,Positron) => ["S"]` : 入射陽電子の散乱
      * `(Electron,Electron) => ["S"]` : 入射電子の散乱
      * `(Positron,Electron) => ["P"]` : 入射陽電子による電子の生成
      * `(Electron,Electron) => ["P"]` : 入射電子による電子の生成
