FermiSurfaceは1つのフェルミ面に関する情報をエンコードします。通常、Marching Tetrahedra法から構築されます。

# フィールド

  * `rlat::SMatrix{3,3,Float64,9}`、列に格納された逆格子ベクトル
  * `ks::Matrix{Float64}`、フェルミ面上の縮小k点のリスト。
  * `faces::Matrix{Int64}`、フェルミ面上の隣接するk点を接続する三角形のセット。
  * `weights::Vector{Float64}`、各k点に関連付けられた面積。
  * `bandidx::Union{Missing,Int64}`、バンドインデックス。

# 構築メソッド

```julia
FermiSurface(rlat::AbstractMatrix{<:Real}, ks::AbstractMatrix{<:Real}, faces::AbstractMatrix{<:Integer})
```
