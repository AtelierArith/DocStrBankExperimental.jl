```
geocode(geocoder::Geocoder, query::AbstractString; kwargs...)::Response
```

場所の名前や住所を座標に変換するためのフォワードジオコーディングを実行します。

# 引数

  * `geocoder::Geocoder`: リクエストに使用するジオコーダーインスタンス
  * `query::AbstractString`: ジオコーディングする場所の名前または住所
  * `kwargs...`: APIに渡すオプションのパラメータ

# オプションのパラメータ

  * `language::AbstractString`: 結果のための優先言語
  * `countrycode::Union{AbstractString, Vector{<:AbstractString}}`: 特定の国に結果を制限
  * `bounds::NTuple{4, Number}`: 結果をバウンディングボックス内に制限 (min*lng, min*lat, max*lng, max*lat)
  * `proximity::NTuple{2, Number}`: 特定の場所に結果をバイアス (lat, lng)
  * `limit::Integer`: 返す結果の最大数
  * `no_annotations::Bool`: 結果から注釈を除外
  * `no_record::Bool`: クエリをOpenCageデータベースに保存しない
  * その他多数 (OpenCage APIドキュメントを参照)

# 戻り値

  * `Response`: ジオコーディング結果を含むAPIレスポンス

# 例外

  * `InvalidInputError`: クエリが空の場合
  * `NotAuthorizedError`: APIキーが無効な場合
  * `RateLimitExceededError`: レート制限を超えた場合
  * `NetworkError`: ネットワークエラーが発生した場合
  * その他の`OpenCageError`サブタイプによるさまざまなエラー条件

# 例

```julia
geocoder = Geocoder("your-api-key")
response = geocode(geocoder, "Berlin, Germany")

# オプションのパラメータを使用
response = geocode(geocoder, "London",
    language="fr",
    countrycode="gb",
    limit=5,
    no_annotations=true
)
```
