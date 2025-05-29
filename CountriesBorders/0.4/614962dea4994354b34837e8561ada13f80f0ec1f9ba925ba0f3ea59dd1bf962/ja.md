```
extract_countries([geotable::GeoTables.GeoTable]; skip_areas = nothing, kwargs...)
extract_countries(admin::Union{AbstractString, Vector{<:AbstractString}}; skip_areas = nothing, kwargs...)
```

検索クエリを通じて提供された `kwargs` に一致するすべての国を含むドメイン（`<:Meshes.Domain`）を抽出して返します...

返された `domain` は、[`SimpleLatLon`](@ref) インスタンスとして表現されたポイントの包含をチェックするために使用することができ、また、PlotlyBase と依存パッケージ（例：PlutoPlotly、PlotlyJS）からの `scattergeo` を使用して直接プロットすることもできます。

この関数はカスタム `geotable` を入力として受け取ることができますが、通常は指定せずに呼び出され、その場合はパッケージによってデフォルトでロードされるものを使用します。これは、[naturalearthdata.com](https://www.naturalearthdata.com/) の1/110mマップから取得されます。具体的には、国境の座標を取得するために使用されるシェイプファイルは、[https://github.com/nvkelso/natural-earth-vector/blob/ca96624a56bd078437bca8184e78163e5039ad19/geojson/ne*110m*admin*0*countries_lakes.geojson](https://github.com/nvkelso/natural-earth-vector/blob/ca96624a56bd078437bca8184e78163e5039ad19/geojson/ne_110m_admin_0_countries_lakes.geojson) にあります。

`geotable` には、国ごとに1行と、さまざまな国関連情報が列として含まれています。

ドメインを形成するための国の選択は、`String` または `Vector{String}` 値を含むキーワード引数を渡すことによって行われます。

# 拡張ヘルプ

## 入力解析

各キーワード引数について、関数はキーワード引数名と一致する `geotable` 列に対して選択を行います。選択は、提供された文字列を値として基に行われます：

  * 文字列は、テーブルの各行の指定された列の値と完全名（大文字と小文字を区別しない）を一致させるために使用されます。
  * 文字列内で `*` ワイルドカードを使用して、任意の数の単語またはスペース文字に展開できます。
  * 文字列が '-' 文字で始まる場合、一致するすべての行が現在の選択から削除されます。そうでない場合、一致する行が選択に追加されます（文字列の前に '+' を置くことで、削除ではなく追加を強調することもできます）。
  * 各キーワード引数に対して、複数のクエリ/一致文字列を提供することもでき、文字列のベクターとして、または同じ文字列内で ';' で区切って提供できます。

      * 複数のクエリは、提供された順序で処理され、合計選択に応じて追加または削除されます。
  * 各キーワード引数は、提供された順序で処理され、前述のポイントに従って選択を変更します。
  * キーワード引数の名前は、`shapefile` の列名と一致させるためにすべて大文字にされます。デフォルトテーブルの列名はすべて大文字であるため、`extract_countries(;ConTinEnt = "Asia")` を呼び出すと、`shapefile` の `:CONTINENT` 列と一致します。

### 解析例

  * `extract_countries(;continent = "europe", admin="-russia")` は、ロシアを除くヨーロッパ大陸内のすべての国の境界を抽出します。
  * `extract_countries(;admin="-russia", continent = "europe")` は、ロシアを含むヨーロッパ大陸内のすべての国の境界を抽出します。これは、文字列が順番に処理されるため、ロシアが最初に削除され、その後ヨーロッパ（ロシアを含む）が追加されるためです。
  * `extract_countries(;subregion = "*europe; -eastern europe")` は、`subregion` 名が `europe` で終わるすべての国を抽出します（北部、東部、西部、南部を含む）が、`eastern europe` サブリージョン内の国は含まれません。

可能な列名のリストについては、関数 `CountriesBorders.valid_column_names()` を呼び出してください。

最も便利な列名のいくつかに含まれる可能な値のリストについては、関数 `CountriesBorders.possible_selector_values()` を呼び出してください。

## エリアのスキップ

上記の文字列解析構文を使用してエリアを削除することに加えて、`skip_area` キーワード引数を使用して、国（`ADMIN` 名に基づく）または国のサブエリアのリストを提供することもできます。

提供された `skip_area` は、次の要素の配列でなければなりません：

  * `SkipDict` のインスタンス
  * `SkipFromAdmin` のインスタンス
  * `SkipFromAdmin` オブジェクトを直接構築するために使用できるオブジェクトのインスタンス：

      * 単一の `String`。（提供された `String` を `admin` とし、コロン（:）を2番目の引数とする `SkipFromAdmin` に変換されます）
      * `Tuple{<:AbstractString, <:Any}` のインスタンス `t` の場合、結果の `SkipFromAdmin` は `SkipFromAdmin(t...)` として作成されます。

提供された要素は、`extract_countries` の名目出力から削除されるスキップする国/エリアの単一リストにマージされます。

スキップするためのデフォルトの非大陸EUエリアのセットは、エクスポートされた定数 `SKIP_NONCONTINENTAL_EU` に利用可能で、`skip_areas` 引数として渡すことができます（または `skip_areas` に渡される配列の要素の1つとして）。

### 例

```jldoctest
julia> using CountriesBorders

julia> dmn = let
        # 次のコードは、フランス領ギアナ（フランスの一部）、シチリア、スヴァールバル諸島（ノルウェーの一部）を除いて、イタリア、フランス、ノルウェーの境界を抽出します。
        extract_countries("italy; spain; france; norway"; skip_areas = [
            ("Italy", 2) # これは、イタリアの MultiPolyArea の2番目のポリゴンを削除します。これはシチリアに対応します。
            "Spain" # これは、スペイン全体を削除します。
            SKIP_NONCONTINENTAL_EU # これは、スヴァールバルとフランス領ギアナを削除します。
        ])
       end
3 view(::GeometrySet{CountryBorder{Float32}}, resolution = 110m, [22, 44, 142])
├─ ノルウェー (3 スキップ)
├─ フランス (1 スキップ)
└─ イタリア (1 スキップ)

julia> catania = LatLon(37.5, 15.09) # シチリアのカターニアの位置
GeodeticLatLon{WGS84Latest} 座標
├─ 緯度: 37.5°
└─ 経度: 15.09°

julia> Point(catania) in dmn # これは false を返します。シチリアはドメインから除外されています。
false

julia> rome = LatLon(41.9, 12.49) # ローマ
GeodeticLatLon{WGS84Latest} 座標
├─ 緯度: 41.9°
└─ 経度: 12.49°

julia> Point(rome) in dmn # これは true を返します。
true
```
