```
mutate([client::Client], mutation_name::Union{Alias, AbstractString}, args::AbstractDict, output_type::Type=Any; kwargs...)
```

サーバーでミューテーションを実行します。`client`が指定されていない場合は、グローバルクライアントが使用されます。

`output_fields`が指定されていない場合、何も返されません。

デフォルトでは、`mutate`は`GQLReponse{Any}`を返し、個々のミューテーションのデータは`gql_response.data[mutation_name]`で見つけることができます。

ミューテーションは`client`の`endpoint`フィールドを使用します。

# 引数

  * `client::Client`: GraphQLクライアント（オプション）。指定されていない場合は、[`global_graphql_client`](@ref)が使用されます。
  * `mutation_name::Union{Alias, AbstractString}`: ミューテーション名。
  * `args`: ミューテーション引数のキーと値のペアの辞書 - 辞書やベクターでネスト可能です。
  * `output_type::Type=Any`: クエリ応答オブジェクトの出力データ型。`GQLResponse{output_type}`型のオブジェクトが返されます。詳細については、`GQLResponse`のドキュメントを参照してください。

# キーワード引数

  * `output_fields=String[]`: 返される出力フィールド。文字列、または辞書やベクターで構成されることができます。
  * `direct_write=false`: `true`の場合、クエリは`args`から直接文字列を生成して形成され、イントロスペクションされたスキーマは使用されません。ENUMは`GQLEnum`でラップする必要があります。詳細については、[`directly_write_query_args`](@ref)を参照してください。
  * `retries=1`: エラーが発生する前にミューテーションが試行される回数。
  * `readtimeout=0`: HTTPリクエストのタイムアウト長。タイムアウトなしにするには0に設定します。
  * `throw_on_execution_error=false`: `true`に設定すると、GraphQLサーバーの応答に実行中に発生したエラーが含まれている場合に例外がスローされます。

参照: [`GQLResponse`](@ref)
