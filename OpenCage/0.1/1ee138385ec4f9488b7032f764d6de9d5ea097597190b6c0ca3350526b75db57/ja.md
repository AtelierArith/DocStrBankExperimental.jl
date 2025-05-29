```
reverse_geocode(geocoder::Geocoder, latitude::Number, longitude::Number; kwargs...)::Response
```

座標を場所名または住所に変換するための逆ジオコーディングを実行します。

# 引数

  * `geocoder::Geocoder`: リクエストに使用するジオコーダーインスタンス
  * `latitude::Number`: 緯度座標
  * `longitude::Number`: 経度座標
  * `kwargs...`: APIに渡すオプションのパラメータ

# オプションのパラメータ

  * `language::AbstractString`: 結果のための優先言語
  * `no_annotations::Bool`: 結果から注釈を除外する
  * `no_record::Bool`: クエリをOpenCageデータベースに保存しない
  * その他多数（OpenCage APIドキュメントを参照）

# 戻り値

  * `Response`: ジオコーディング結果を含むAPIレスポンス

# 例外

  * `InvalidInputError`: 座標が無効な場合
  * `NotAuthorizedError`: APIキーが無効な場合
  * `RateLimitExceededError`: レート制限を超えた場合
  * `NetworkError`: ネットワークエラーが発生した場合
  * その他のさまざまなエラー条件に対する`OpenCageError`のサブタイプ

# 例

```julia
geocoder = Geocoder("your-api-key")
response = reverse_geocode(geocoder, 52.5200, 13.4050)

# オプションのパラメータを使用
response = reverse_geocode(geocoder, 51.5074, -0.1278,
    language="fr",
    no_annotations=true
)
```
