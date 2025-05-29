```
struct PointMassSystem
```

カイトシステムの離散質量-ばね-ダンパー表現であり、点質量が弾性セグメントで接続されてカイトとテザーのダイナミクスをモデル化します：

  * `points::Vector{Point}`: 次のことを表す点質量：

      * カイトの取り付けポイント
      * 動的ブライドル/テザーのポイント
      * 固定された地面のアンカーポイント
  * `groups::Vector{KitePointGroup}`: カイトの変形（ねじれと後縁の変位）に応じて一緒に動くポイントのコレクション
  * `segments::Vector{Segment}`: ポイント間のばね-ダンパー要素
  * `pulleys::Vector{Pulley}`: ラインの長さを再分配する要素
  * `tethers::Vector{Tether}`: 共通の未伸張長を持つセグメントのグループ
  * `winches::Vector{Winch}`: テザーの長さを制御する地上ベースのウインチ

参照： [`Point`](@ref), [`Segment`](@ref), [`KitePointGroup`](@ref), [`Pulley`](@ref)
