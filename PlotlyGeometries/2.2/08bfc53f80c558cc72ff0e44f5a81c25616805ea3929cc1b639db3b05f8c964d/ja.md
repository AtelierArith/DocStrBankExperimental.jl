```
squares(origin::Vector{<:Real}, side::Real, color::String="", mode::String="z"; opc::Real=1)

指定された原点を中心に、指定された辺の長さと色を持つ2D正方形メッシュを作成します。

# 引数
- `origin::Vector{<:Real}`: 正方形の中心を指定する3つのRealのベクトル。
- `side::Real`: 正方形の辺の長さを指定するReal。
- `color::String`: 正方形の色を指定する文字列。
- `mode`::String: (オプション) 正方形の向きを指定する文字列 ("x", "y", または "z")。デフォルトは "z"。

# キーワード
- `opc`: (オプション) 正方形の不透明度を指定するReal。デフォルトは1。
```
