```
create_cube(origin::Vector{<:Real}, dim::Real, ind::Int=1, mode::String="corner", fac::Real=2; render=false)

指定されたパラメータで立方体を作成します。

# 引数
- `origin::Vector{<:Real}`: 立方体の原点。
- `dim::Real`: 立方体の辺の長さ。
- `ind::Int=1`: 立方体の色インデックス。
- `mode::String="corner"`: 立方体の原点を指定するモード（"corner"または"center"）。
- `fac::Real=2`: グリッド間隔に応じた内部密度化係数。

# キーワード
- `render=false`: 作成/操作のためのリアルタイムレンダリング。
```
