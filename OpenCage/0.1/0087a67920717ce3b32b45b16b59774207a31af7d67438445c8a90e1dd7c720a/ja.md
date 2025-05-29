```
reverse_geocode_async(geocoder::Geocoder, latitude::Number, longitude::Number; kwargs...)::Task{Response}
```

非同期逆ジオコーディングを実行して、座標を場所名または住所に変換します。

この関数は、結果を取得するために待機または取得できる`Task`を返します。

# 引数

  * `geocoder::Geocoder`: リクエストに使用するジオコーダーインスタンス
  * `latitude::Number`: 緯度座標
  * `longitude::Number`: 経度座標
  * `kwargs...`: APIに渡すオプションのパラメータ（`reverse_geocode`と同じ）

# 戻り値

  * `Task{Response}`: APIレスポンスに解決されるタスク

# 例外

  * `InvalidInputError`: 座標が無効な場合
  * タスクが待機/取得されるときに他の例外がスローされる可能性があります

# 例

```julia
geocoder = Geocoder("your-api-key")
task = reverse_geocode_async(geocoder, 52.5200, 13.4050)

# 他の作業を行う...

# 必要なときに結果を取得
response = fetch(task)
```
