```
lines(pt1::Vector{<:Real}, pt2::Vector{<:Real}, color::String; opc::Real=1, style="")

2つの点の間に3Dラインを作成します。

# 引数
- `pt1::Vector{<:Real}`: ラインの始点。
- `pt2::Vector{<:Real}`: ラインの終点。
- `color::String`: ラインの色。

# キーワード
- `opc`: ラインの不透明度。デフォルトは1。
- `style`: ラインスタイル（例："solid", "dash"）。デフォルトは""。
```
