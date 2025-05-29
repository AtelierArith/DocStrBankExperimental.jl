create_sphere(origin::Vector{<:Real}, radius::Real, ind::Int=1, fac::Real=2; render=false)

指定されたパラメータで球を作成します。

# 引数

  * `origin::Vector{<:Real}`: 球の原点。
  * `radius::Real`: 球の半径。
  * `ind::Int=1`: 球の色インデックス。
  * `fac::Real=2`: グリッド間隔に応じた内部密度化係数。

# キーワード

  * `render=false`: 作成/操作のためのリアルタイムレンダリング。
