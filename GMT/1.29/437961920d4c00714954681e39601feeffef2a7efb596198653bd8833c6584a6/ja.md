```
struct GMTfv{T<:AbstractFloat} <: AbstractMatrix{T}
```

GMTfv構造体は、（主に）三角形メッシュを格納するために使用されます。

この構造体のフィールドは次のとおりです：

  * `verts::Matrix{T}`:         データ頂点を持つMx3行列
  * `faces::Vector{<:Matrix{<:Int}}`:   各行が面である面の行列のベクトル
  * `faces_view::Vector{Matrix{Int}}`:  特定の視点から見える面のみを含む`faces`のサブセット
  * `bbox::Vector{Float64}`:            頂点のバウンディングボックス
  * `color::Vector{Vector{String}}`:    各面のGオプションカラーを持つベクトル
  * `color_vwall::String`:              makecpt cmapオプション引数のための文字列（例："darkgreen,lightgreen"）
  * `zscale::Float64`:                  z値をスケールするための乗数。デフォルトは1。
  * `bfculling::Bool`:                  不可視面のカリングが望ましいかどうか。デフォルトはtrue
  * `isflat::Vector{Bool}`:             これは平面メッシュかどうか。デフォルトはfalse
  * `proj4::String`:                    PROJ4構文の投影文字列（オプション）
  * `wkt::String`:                      WKT構文の投影文字列（オプション）
  * `epsg::Int`:                        EPSG投影コード（オプション）
