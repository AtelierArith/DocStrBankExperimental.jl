```
geocode_async(geocoder::Geocoder, query::AbstractString; kwargs...)::Task{Response}
```

場所名や住所を座標に変換する非同期の前方ジオコーディングを実行します。

この関数は、結果を取得するために待機または取得できる `Task` を返します。

# 引数

  * `geocoder::Geocoder`: リクエストに使用するジオコーダーインスタンス
  * `query::AbstractString`: ジオコーディングする場所名または住所
  * `kwargs...`: APIに渡すオプションのパラメータ（`geocode` と同じ）

# 戻り値

  * `Task{Response}`: APIの応答に解決されるタスク

# 例外

  * `InvalidInputError`: クエリが空の場合
  * タスクが待機/取得される際に他の例外がスローされる可能性があります

# 例

```julia
geocoder = Geocoder("your-api-key")
task = geocode_async(geocoder, "Berlin, Germany")

# 他の作業を行う...

# 必要なときに結果を取得
response = fetch(task)
```
