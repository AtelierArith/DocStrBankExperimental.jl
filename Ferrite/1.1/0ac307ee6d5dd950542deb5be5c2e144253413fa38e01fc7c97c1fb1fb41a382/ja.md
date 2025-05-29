```
PointEvalHandler(grid::Grid, points::AbstractVector{Vec{dim,T}}; kwargs...) where {dim, T}
```

`PointEvalHandler`は、ドメイン内の*任意の点*での関数評価に使用できます - ただし、数値点やノードだけではありません。

コンストラクタは、グリッドと点の座標のベクトルを受け取ります。`PointEvalHandler`は、各点について i) 対応するセル、ii) セル内の（局所的な）座標を計算します。`PointEvalHandler`のフィールドは次のとおりです：

  * `cells::Vector{Union{Int,Nothing}}`: 見つからなかった点には `nothing` が入る、点のセルIDを持つベクトル。
  * `local_coords::Vector{Union{Vec,Nothing}}`: 見つからなかった点には `nothing` が入る、点の局所座標（すなわち、基準構成内の座標）を持つベクトル。

`PointEvalHandler`を使用して関数を評価する方法は2つあります：

  * [`evaluate_at_points`](@ref): 関数が i) `dh::DofHandler` + `uh::Vector`（例えばFE解）で記述されている場合、または ii) `p::L2Projector` + `ph::Vector`（投影データの場合）である場合に使用できます。
  * [`PointIterator`](@ref) + [`PointValues`](@ref)を使用した反復: 点でのより柔軟な評価に使用でき、例えば勾配を計算するために使用できます。
