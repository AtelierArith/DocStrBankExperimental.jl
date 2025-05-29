```
mutable struct GMTdataset{T<:Real, N} <: AbstractArray{T,N}
```

GMTdataset型は、テーブルがGMTおよびGDALライブラリと入出力を行う方法です。これらはAbstractArrayおよびTablesインターフェースを実装しています。

この構造体のフィールドは次のとおりです：

  * `data::Array{T,N}`:             セグメントデータを持つMx2行列
  * `ds_bbox::Vector{Float64}`:     グローバルバウンディングボックス（セグメントが多数ある場合）
  * `bbox::Vector{Float64}`:        セグメントバウンディングボックス
  * `attrib::Dict{String, Union{String, Vector{String}}}`: 属性/値を持つ辞書（オプション）
  * `colnames::Vector{String}`:     列名。将来のTablesインターフェースでの使用を予想
  * `text::Vector{String}`:         データ座標の後にあるテキストを持つ配列（テキストをプロットする際は必須）
  * `header::String`:               セグメントヘッダーを持つ文字列（オプションだが時には非常に便利）
  * `comment::Vector{String}`:      データセットのコメントを持つ配列 [最初のセグメントの後は空]
  * `proj4::String`:                PROJ4構文の投影文字列（オプション）
  * `wkt::String`:                  WKT構文の投影文字列（オプション）
  * `epsg::Int`:                    EPSG投影コード（オプション）
  * `geom::Integer`:                幾何学的タイプ。GDALの列挙型の1つ（wkbPoint、wkbPolygonなど...）
