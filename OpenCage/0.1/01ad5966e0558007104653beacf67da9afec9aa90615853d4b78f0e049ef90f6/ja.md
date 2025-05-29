```
ジオコーダー
```

OpenCageジオコーディングAPIのクライアントです。

`Geocoder`構造体は、OpenCageジオコーディングAPIへのリクエストを行うためのAPIキーと設定オプションを保持します。

# フィールド

  * `api_key::String`: OpenCage APIキー
  * `api_base_url::String`: OpenCage APIのベースURL
  * `user_agent::String`: リクエストに使用するUser-Agent文字列
  * `timeout::Float64`: リクエストのタイムアウト（秒）
  * `retries::Int`: 失敗したリクエストの再試行回数
  * `retry_options::Dict{Symbol, Any}`: 再試行の動作に関するオプション
  * `extra_http_options::Dict{Symbol, Any}`: 追加のHTTPオプション

# コンストラクタ

```julia
Geocoder(
    api_key::AbstractString;
    api_base_url::AbstractString = "https://api.opencagedata.com/geocode/v1/json",
    user_agent_comment::Union{AbstractString, Nothing} = nothing,
    timeout::Real = 60.0,
    retries::Integer = 5,
    retry_options::Dict = Dict{Symbol, Any}(:max_delay => 60.0, :factor => 1.0, :jitter => 0.1),
    extra_http_options::Dict = Dict{Symbol, Any}()
)
```

指定されたAPIキーとオプションを使用して新しい`Geocoder`を作成します。

```julia
Geocoder(; kwargs...)
```

`OPENCAGE_API_KEY`環境変数からAPIキーを使用して新しい`Geocoder`を作成します。

# 例

```julia
# 明示的なAPIキーを使用
geocoder = Geocoder("your-api-key")

# 環境変数を使用
ENV["OPENCAGE_API_KEY"] = "your-api-key"
geocoder = Geocoder()

# カスタムオプションを使用
geocoder = Geocoder(
    "your-api-key",
    timeout=30.0,
    retries=3,
    user_agent_comment="MyApp/1.0"
)
```
