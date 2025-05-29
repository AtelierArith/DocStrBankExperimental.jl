```
Client(endpoint; headers=Dict(), introspect=true)
Client(endpoint, ws_endpoint; headers=Dict(), introspect=true)
```

GraphQLクライアント。`endpoint`のみが提供される場合、`ws_endpoint`は"http"が"ws"に置き換えられた同じものと見なされます。

デフォルトでは、クライアントでイントロスペクションが実行されます。これは、`introspect`キーワード引数を`false`に設定することでオフにできます。

# フィールド - 公開インターフェース

  * `endpoint::String`: クエリとミューテーションのためのエンドポイント。
  * `ws_endpoint::String`: サブスクリプションのためのエンドポイント。
  * `headers::Dict`: クライアント特有のヘッダーを含む。
  * `introspection_complete::Bool`: イントロスペクションが実行された後に`true`に設定される。
  * `queries::Vector{String}`: 利用可能なクエリのリスト。
  * `mutations::Vector{String}`: 利用可能なミューテーションのリスト。
  * `subscriptions::Vector{String}`: 利用可能なサブスクリプションのリスト。

# フィールド - 内部使用

  * `type_to_fields_map::Dict{String, Dict{String, Dict{String, Any}}}`: GQLタイプをそのフィールドにマッピングする。
  * `query_to_type_map::Dict{String, String}`: GQLクエリ、ミューテーション、サブスクリプションをその出力のタイプにマッピングする。
  * `query_to_args_map::Dict{String, Dict{String, String}}`: GQLクエリ、ミューテーション、サブスクリプションをその引数とタイプにマッピングする。
  * `input_object_fields_to_type_map::Dict{String, Dict{String, String}}`: GQL入力オブジェクトをそのフィールド/タイプにマッピングする。
  * `schema::Dict{String, Any}`: サーバーの完全なスキーマ。
  * `introspected_types::Dict{String, DataType}`: すべてのイントロスペクションされたタイプを含む辞書。

# 例

```julia
julia> client = Client("https://countries.trevorblades.com")
GraphQLClient Client
       endpoint: https://countries.trevorblades.com
    ws_endpoint: wss://countries.trevorblades.com

julia> client = Client("https://countries.trevorblades.com", "wss://countries.trevorblades.com")
GraphQLClient Client
       endpoint: https://countries.trevorblades.com
    ws_endpoint: wss://countries.trevorblades.com
```
