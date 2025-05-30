# GeoJSON

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaGeo.github.io/GeoJSON.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://JuliaGeo.github.io/GeoJSON.jl/dev) [![CI](https://github.com/JuliaGeo/GeoJSON.jl/workflows/CI/badge.svg)](https://github.com/JuliaGeo/GeoJSON.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaGeo/GeoJSON.jl/branch/main/graph/badge.svg?token=ccpOaPSi08)](https://codecov.io/gh/JuliaGeo/GeoJSON.jl)

[GeoJSON](https://geojson.org/)ファイルを[JSON3.jl](https://github.com/quinnj/JSON3.jl)を使用して読み込み、[Tables.jl](https://github.com/JuliaData/Tables.jl)インターフェースを提供します。

このパッケージは、一般的なJSON形式のために同じことを行う[JSONTables.jl](https://github.com/JuliaData/JSONTables.jl)から多くのコードを借用し、強くインスパイアされています。GeoJSONは、ジオメトリを`geometry`列に配置し、すべてのプロパティを個別の列に追加します。

## 使用法

GeoJSONは、シンプルな`read`および`write`メソッドのみを提供します。`GeoJSON.read`は、ファイルパス、文字列、IO、またはバイトを受け取ります。

```julia
julia> using GeoJSON, DataFrames

julia> fc = GeoJSON.read("path/to/a.geojson")
FeatureCollection with 171 Features

julia> first(fc)
Feature with geometry type Polygon and properties Symbol[:geometry, :timestamp, :version, :changeset, :user, :uid, :area, :highway, :type, :id]

# Tablesインターフェースを使用して形式を変換したり、データを抽出したり、行を反復処理したりします
julia> df = DataFrame(fc)

# 文字列に書き込む
julia> write(fc)
"{\"type\":\"FeatureCollection\",\"features\":[{\"type\":\"Feature\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-69.99693762899992...
```

### HTTPアクセス

URLからJSONを読み込むには、HTTP.jlを使用します。

```julia

julia> using GeoJSON, HTTP

julia> resp = HTTP.get("https://path/to/file.json")

julia> fc = GeoJSON.read(resp.body)
```
