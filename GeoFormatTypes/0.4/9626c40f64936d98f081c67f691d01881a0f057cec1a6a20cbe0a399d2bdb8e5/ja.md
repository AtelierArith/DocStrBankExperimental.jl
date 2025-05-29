# GeoFormatTypes

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaGeo.github.io/GeoFormatTypes.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://JuliaGeo.github.io/GeoFormatTypes.jl/dev) [![CI](https://github.com/JuliaGeo/GeoFormatTypes.jl/workflows/CI/badge.svg)](https://github.com/JuliaGeo/GeoFormatTypes.jl/actions?query=workflow%3ACI)

GeoFormatTypesは、Well Known TextやGeoJSONなどの地理フォーマットをパッケージ間で簡単に渡したり、ディスパッチしたりするためのラッパータイプを定義します。この方法により、含まれているフォーマットに関する情報が後で使用できるように保持されます。 - 代わりに、何を意味するか分からない`String`や`Int`を渡すのではなく。

ラッパータイプは、`convert`のようなメソッドが複数のフォーマットのデータで機能することを可能にし、フォーマット固有の処理メソッドのリストを定義する代わりに使用されます。現在、ArchGDAL.jlはGDALを使用してGeoFormatTypes.jlオブジェクトの`convert`メソッドを定義する特権を持っています。これが読み込まれると、オブジェクトはあるフォーマットから別のフォーマットに変換できます：

```julia
julia> using GeoFormatTypes, ArchGDAL

julia> convert(WellKnownText, EPSG(4326))
WellKnownText{GeoFormatTypes.CRS, String}(GeoFormatTypes.CRS(), "GEOGCS[\"WGS 84\",DATUM[\"WGS_1984\",SPHEROID[\"WGS 84\",6378137,298.257223563,AUTHORITY[\"EPSG\",\"7030\"]],AUTHORITY[\"EPSG\",\"6326\"]],PRIMEM[\"Greenwich\",0,AUTHORITY[\"EPSG\",\"8901\"]],UNIT[\"degree\",0.0174532925199433,AUTHORITY[\"EPSG\",\"9122\"]],AXIS[\"Latitude\",NORTH],AXIS[\"Longitude\",EAST],AUTHORITY[\"EPSG\",\"4326\"]]")
```

ArchGDAL.jlはGeoFormatTypes.jlの直接の依存関係ではないため、地理空間フォーマットを何らかの方法で処理する小さなパッケージは、大きな依存関係を気にせずにGeoFormatTypes.jlに依存できます。

`GeoFormat`オブジェクトの一つの複雑さは、いくつかのフォーマットがCRS（座標参照系）または幾何データ、またはその両方を同時に保持できることです。

これは、`CRS`、`Geom`、および`Mixed`の特性を使用して処理されます。内容が明示的に例えばcrsデータであることが知られている場合、`CRS`を使用できます。例えば、すべてのタイプのウェルノウンテキストで：

```julia
crs = WellKnownText2(CRS(), crs_string)
```

内容が不明な場合、デフォルトの`Mixed()`はほとんどの場合正しいことを行います - 含まれているデータで実際に可能であれば、`convert`を使用してCRSまたは幾何フォーマットに変換できます。

このパッケージへの貢献を支援してくれたJulia Computingに感謝します。
