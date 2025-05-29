```
mutable struct GMTgrid{T<:Number,N} <: AbstractArray{T,N}
```

GMTgrid型は、2Dまたは多層のグリッドが、(地理的に)参照されているかどうかにかかわらず、GMTおよびGDALライブラリと入出力を行う方法です。これらはAbstractArrayインターフェースを実装しています。

この構造体のフィールドは次のとおりです：

  * `proj4::String`:                      PROJ4構文の投影文字列（オプション）
  * `wkt::String`:                        WKT構文の投影文字列（オプション）
  * `epsg::Int`:                          EPSGコード
  * `geog::Int`:                          地理座標か？ 0 -> いいえ; 1 -> [-180 180]; 2 -> [0 360]
  * `range::Vector{Float64}`:             1x6[8]ベクトルで[x*min, x*max, y*min, y*max, z*min, z*max [, v*min, v*max]]
  * `inc::Vector{Float64}`:               1x2[3]ベクトルで[x*inc, y*inc [,v_inc]]
  * `registration::Int`:                  登録タイプ：0 -> グリッド登録; 1 -> ピクセル登録
  * `nodata::Union{Float64, Float32}`:    nodataの値
  * `title::String`:                      タイトル（オプション）
  * `comment::String`:                    コメント（オプション）
  * `command::String`:                    グリッドを作成するために使用されたコマンド（オプション）
  * `cpt::String`:                        このグリッドの推奨GMT CPT名
  * `names::Vector{String}`:              多層を使用するため、かつレイヤーに名前がある場合（オプション）
  * `x::Vector{Float64}`:                 [1 x n_columns]ベクトルでXX座標
  * `y::Vector{Float64}`:                 [1 x n_rows]    ベクトルでYY座標
  * `v::Union{Vector{<:Real}, Vector{String}}`:    [v x n_bands]   ベクトルでVV（3Dグリッド用の垂直）座標
  * `z::Array{T,N}`:                      [n*rows x n*columns]グリッド配列
  * `x_unit::String`:                     XX軸の単位（オプション）
  * `y_unit::String`:                     YY軸の単位（オプション）
  * `v_unit::String`:                     垂直軸の単位（オプション）
  * `z_unit::String`:                     z値の単位（オプション）
  * `layout::String`:                     グリッドメモリレイアウトを説明する3文字の文字列
  * `scale::Union{Float64, Float32}=1f0`: ファイルに保存する際に`z = z * scale + offset`を適用
  * `offset::Union{Float64, Float32}=0f0`
  * `pad::Int=0`:                         0でない場合、配列がPAD行/列のパディングされた配列に配置されることを意味します
  * `hasnans::Int=0`:                     0 -> "わからない"; 1 -> 確認済み、"NaNはない"; 2 -> 確認済み、"NaNがある"
