```
D = geocoder(address::String; options=String[]) => GMTdataset
```

指定された住所のジオコーダー情報を取得するには、GDAL/OGRジオコーディング関数を呼び出します。詳細は https://gdal.org/doxygen/ogr__geocoding_8h.html を参照してください。

### 引数

  * `address`: ジオコーディングする文字列。
  * `options`: これらはGDALに渡されるオプションで、文字列のベクターの形式です。たとえば、デフォルトは `options=["SERVICE", "OSM_NOMINATIM"]` と同等です。

      * "CACHE*FILE" : デフォルトは "ogr*geocode*cache.sqlite"（SQLiteドライバが利用できない場合は "ogr*geocode_cache.csv"）。任意のCSV、SQLite、またはPostgreSQLデータソースである可能性があります。
      * "READ_CACHE" : "TRUE"（デフォルト）または "FALSE"
      * "WRITE_CACHE" : "TRUE"（デフォルト）または "FALSE"
      * "SERVICE": "OSM*NOMINATIM"（デフォルト）、"MAPQUEST*NOMINATIM"、"YAHOO"、"GEONAMES"、"BING" またはその他の値。注意: "YAHOO"はもはや無料サービスとして利用できません。
      * "EMAIL": OSM_NOMINATIMによって使用されます。オプションですが、推奨されます。
      * "USERNAME": GEONAMESによって使用されます。その場合は必須です。
      * "KEY": BINGによって使用されます。その場合は必須です。
      * "APPLICATION": User-Agent MIMEヘッダーを設定するために使用されます。デフォルトはGDAL/OGRのバージョン文字列です。
      * "LANGUAGE": Accept-Language MIMEヘッダーを設定するために使用されます。検索結果を表示するための優先言語順序。
      * "DELAY": 2つの連続したクエリの間の最小遅延（秒単位）。デフォルトは1.0です。
      * "QUERY*TEMPLATE": GETリクエストのURLテンプレート。%sが1回だけ含まれている必要があります。指定されていない場合、SERVICE=OSM*NOMINATIM、MAPQUEST_NOMINATIM、YAHOO、GEONAMESまたはBINGの場合、URLテンプレートはハードコーディングされています。
      * "REVERSE*QUERY*TEMPLATE": 逆ジオコーディングのGETリクエスト用のURLテンプレート。{lon}と{lat}が1回だけ含まれている必要があります。指定されていない場合、SERVICE=OSM*NOMINATIM、MAPQUEST*NOMINATIM、YAHOO、GEONAMESまたはBINGの場合、URLテンプレートはハードコーディングされています。

### 戻り値

入力住所に対してジオコーダーから返された経度、緯度、および完全な属性辞書を含むGMTdataset。 このデータセットには1つのポイントのみが含まれていますが、ジオコーディングサービスはそのポイントを含むBoundingBoxも返します。 `address`が非常に特定のものである場合、そのBBはポイントの周りに小さくなりますが、クエリが一般的な場合（たとえば、都市名や国名のみ）、BBは大きくなり、`mosaic`プログラムで使用するのに非常に便利です。その目的のために、返されたBBはGMTdatasetの$ds_bbox$フィールドに保存されます。

### 例

```
geocoder("Paris, France")
```
