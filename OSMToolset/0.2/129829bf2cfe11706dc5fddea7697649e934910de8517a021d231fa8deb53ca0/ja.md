```
OSM XMLからのデータスクレイピングプロセスの構成を表します。
```

ここで定義されたデータのみがスクレイピングされます。

構成は、次の列を持つDataFrameで定義されます: `group`, `key`, `values`, `influence`, `range`。DataFrameの代わりにCSVファイルへのパスを提供することもできます。

### コンストラクタ

  * `ScrapePOIConfig()` - データスクレイピングのためのデフォルトの組み込み構成。デフォルトの構成はライブラリの更新に伴い変更される可能性があることに注意してください。これにより、デフォルトの構成と`AttractivenessMetaPOI`がメタデータとして使用されます。
  * `ScrapePOIConfig(keys::Union{Tuple{String,String}, String}...)` - スクレイピングのためのキーを提供し、`NoneMetaPOI`がメタデータとして使用されます。
  * `ScrapePOIConfig(pairs::Pair{<:Union{Tuple{String,String}, String}, T}...)` - キーと対応するメタデータを提供します。
  * `ScrapePOIConfig{T <: AbstractMetaPOI}(df::DataFrame)` - 構成として`DataFrame`を使用します。
  * ScrapePOIConfig{T <: AbstractMetaPOI}(meta::Dict{<:Union{String, Tuple{String,String}}, T}) - 内部コンストラクタ。`meta`辞書は、単一の`k="keyname"`値または値のタプル（`v="valuename"`とペア）を魅力的なメタデータにどのようにマッピングするかを説明します。

### 例

```julia
ScrapePOIConfig(("amenity", "parking"), ("parking"))

ScrapePOIConfig(("*", "restaurant"))

ScrapePOIConfig("*")

ScrapePOIConfig(("amenity", "parking") =>AttractivenessMetaPOI(:car, 1, 500), ("amenity", "restaurant") => (AttractivenessMetaPOI(:food, 1.0, 1000.0)))

ScrapePOIConfig([("amenity", "pub"), ("amenity", "restaurant")] .=> Ref(AttractivenessMetaPOI(:food, 1.0, 100.0)))
```
