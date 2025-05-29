```
cuboids(origin::Vector{<:Real}, dimension::Vector{<:Real}, color::String=""; opc::Real=1)

指定された原点を中心に、指定された寸法と色の3Dボックスメッシュを作成します。

# 引数
- `origin::Vector{<:Real}`: ボックスの中心を指定する3つのRealのベクトル。
- `dimension::Vector{<:Real}`: ボックスの寸法（幅、高さ、奥行き）を指定する3つのRealのベクトル。
- `color::String`: ボックスの色を指定する文字列。

# キーワード
- `opc`: （オプション）ボックスの不透明度を指定するReal。デフォルトは1。
```
