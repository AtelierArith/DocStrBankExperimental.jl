```
mutable struct GMTimage{T<:Union{Unsigned, Bool}, N} <: AbstractArray{T,N}
```

GMTimage型は、画像（UInt8、UInt16）、2Dまたはマルチレイヤー、（地理的に）参照されるかどうかにかかわらず、GMTおよびGDALライブラリとの入出力を行う方法です。これらはAbstractArrayインターフェースを実装しています。

この構造体のフィールドは次のとおりです：

  * `proj4::String`:              PROJ4構文の投影文字列（オプション）
  * `wkt::String`:                WKT構文の投影文字列（オプション）
  * `epsg::Int`:                  EPSGコード
  * `geog::Int`:                  地理座標ですか？ 0 -> いいえ; 1 -> [-180 180]; 2 -> [0 360]
  * `range::Vector{Float64}`:     1x6[8]ベクトルで[x*min, x*max, y*min, y*max, z*min, z*max [, v*min, v*max]]
  * `inc::Vector{Float64}`:       1x2[3]ベクトルで[x*inc, y*inc [,v_inc]]
  * `registration::Int`:          登録タイプ：0 -> グリッド登録; 1 -> ピクセル登録
  * `nodata::Float32`:            nodataの値
  * `color_interp::String`:       "Gray"と等しい場合、cmapなしのインデックス画像は灰色のcmapを取得します
  * `metadata::Vector{String}`:   最終的にGDALに渡される可能性のあるメタデータを格納するためのもの（オプション）
  * `names::Vector{String}`:      マルチバンドでバンドに名前がある場合に使用するためのもの（オプション）
  * `x::Vector{Float64}`:         [1 x n_columns]ベクトルでXX座標
  * `y::Vector{Float64}`:         [1 x n_rows]    ベクトルでYY座標
  * `v::Vector{Float64}`:         [v x n_bands]   垂直座標またはハイパーキューブ内の波長のベクトル（オプション）
  * `image::Array{T,N}`:          [n*rows x n*columns x n_bands]画像配列
  * `labels::Vector{String}`:     カテゴリカルCPTのラベル
  * `n_colors::Int`:              ベクトル'colormap'に保存されている色の数
  * `colormap::Vector{Int32}`:    n_colors-by-4で列ごとに保存されたベクトル
  * `alpha::Matrix{UInt8}`:       [n*rows x n*columns]アルファ配列
  * `layout::String`:             画像メモリレイアウトを説明する4文字の文字列
  * `pad::Int`:                   0でない場合、配列がPAD行/列のパディングされた配列に配置されていることを意味します
