```
cubes(origin::Vector{<:Real}, side::Real, color::String=""; opc::Real=1)

指定された原点を中心に、指定された寸法と色の3Dキューブメッシュを作成します。

# 引数
- `origin::Vector{<:Real}`: キューブの中心を指定する3つのRealのベクトル。
- `side::Real`: キューブの辺の長さ。
- `color::String`: キューブの色を指定する文字列。

# キーワード
- `opc`: (オプション) キューブの不透明度を指定するReal。デフォルトは1。
```
