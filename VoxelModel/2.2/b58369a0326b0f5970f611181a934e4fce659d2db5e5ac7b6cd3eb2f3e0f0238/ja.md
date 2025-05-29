```
create_cuboid(origin::Vector{<:Real}, dim::Vector{<:Real}, ind::Int=1, mode::String="corner", fac::Real=2; render=false)

指定されたパラメータで直方体を作成します。

# 引数
- `origin::Vector{<:Real}`: 直方体の原点。
- `dim::Vector{<:Real}`: 直方体の寸法。
- `ind::Int=1`: 直方体の色インデックス。
- `mode::String="corner"`: 直方体の原点を指定するモード（"corner"または"center"）。
- `fac::Real=2`: グリッド間隔に応じた内部密度化係数。

# キーワード
- `render=false`: 作成/操作のためのリアルタイムレンダリング。
```
