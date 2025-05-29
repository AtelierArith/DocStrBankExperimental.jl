```
query([client::Client], query_name::Union{Alias, AbstractString}, output_type::Type=Any; kwargs...)
```

サーバーにクエリを実行します。`client`が供給されていない場合は、グローバルクライアントを使用します。

`output_fields`が供給されていない場合、すべての可能なフィールド（`client`のイントロスペクションによって決定される）が返されます。

クエリは`client`の`endpoint`フィールドを使用します。

デフォルトでは、`query`は`GQLReponse{Any}`を返し、個々のクエリのデータは`gql_response.data[query_name]`で見つけることができます。

# 引数

  * `client::Client`: GraphQLクライアント（オプション）。供給されていない場合は、[`global_graphql_client`](@ref)が使用されます。
  * `query_name::Union{Alias, AbstractString}`: サーバーのクエリ名。
  * `output_type::Type=Any`: クエリ応答オブジェクトの出力データ型。`GQLResponse{output_type}`型のオブジェクトが返されます。詳細については、`GQLResponse`のドキュメントを参照してください。

# キーワード引数

  * `query_args=Dict()`: クエリ引数のキーと値のペアの辞書 - 辞書やベクターでネスト可能です。
  * `output_fields=String[]`: 返される出力フィールド。文字列、または辞書やベクターで構成されることができます。空の場合、`query`はすべてのフィールドを返そうとします。
  * `direct_write=false`: `true`の場合、クエリは`query_args`から直接文字列を生成して形成され、イントロスペクションされたスキーマは使用されません。ENUMは`GQLEnum`でラップする必要があります。詳細については、[`directly_write_query_args`](@ref)を参照してください。
  * `retries=1`: エラーが発生する前にミューテーションが試行される回数。
  * `readtimeout=0`: HTTPリクエストのタイムアウト長。タイムアウトなしにするには0に設定します。
  * `throw_on_execution_error=false`: GraphQLサーバーの応答に実行中に発生したエラーが含まれている場合に例外をスローするには`true`に設定します。
  * `verbose=0`: 追加のログ記録のために1、2に設定します。

参照: [`GQLResponse`](@ref)
