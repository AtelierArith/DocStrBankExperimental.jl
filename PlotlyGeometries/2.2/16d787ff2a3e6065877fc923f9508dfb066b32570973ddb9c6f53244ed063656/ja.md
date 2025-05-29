```
spheres(origin::Vector{<:Real}, r::Real, color::String=""; opc::Real=1, tres=60, pres=30, ah::Real=0)

3D 球体メッシュを作成します。

# 引数
- `origin::Vector{<:Real}`: 楕円体の中心。
- `r::Real`: 球の半径。
- `color::String`: 楕円体の色。

# キーワード
- `opc`: 楕円体の不透明度。デフォルトは 1。
- `tres`: メッシュグリッドの解像度 (theta)。デフォルトは 60。
- `pres`: メッシュグリッドの解像度 (phi)。デフォルトは 30。
- `ah`: アルファハル値。デフォルトは 0。
```
