```
ellipsoids(origin::Vector{<:Real}, par::Vector{<:Real}, color::String=""; opc::Real=1, tres=61, pres=31, ah::Real=0)

3D楕円体メッシュを作成します。

# 引数
- `origin::Vector{<:Real}`: 楕円体の中心。
- `par::Vector{<:Real}`: 楕円体のパラメータ (a, b, c)。
- `color::String`: 楕円体の色。

# キーワード
- `opc`: 楕円体の不透明度。デフォルトは1。
- `tres`: メッシュグリッドの解像度 (theta)。デフォルトは61。
- `pres`: メッシュグリッドの解像度 (phi)。デフォルトは31。
- `ah`: アルファハル値。デフォルトは0。
```
