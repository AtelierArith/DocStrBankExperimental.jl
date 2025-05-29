create_ellipsoid(origin::Vector{<:Real}, par::Vector{<:Real}, ind::Int=1, fac::Real=2; render=false)

指定されたパラメータで楕円体を作成します。

# 引数

  * `origin::Vector{<:Real}`: 楕円体の原点。
  * `par::Vector{<:Real}`: 半軸の長さ。
  * `ind::Int=1`: 楕円体の色インデックス。
  * `fac::Real=2`: グリッド間隔に応じた内部密度化係数。

# キーワード

  * `render=false`: 作成/操作のためのリアルタイムレンダリング。
