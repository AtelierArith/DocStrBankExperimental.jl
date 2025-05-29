create_cylinder(origin::Vector{<:Real}, radius::Real, height::Real, ind::Int=1, fac::Real=2; render=false)

指定されたパラメータで円柱を作成します。

# 引数

  * `origin::Vector{<:Real}`: 円柱の基点の原点。
  * `radius::Real`: 円柱の半径。
  * `height::Real`: 円柱の高さ。
  * `ind::Int=1`: 円柱の色インデックス。
  * `fac::Real=2`: グリッド間隔に応じた内部密度化係数。

# キーワード

  * `render=false`: 作成/操作のためのリアルタイムレンダリング。
