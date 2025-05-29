```
open_subscription(fn::Function,
                  [client::Client],
                  subscription_name::Union{Alias, AbstractString},
                  output_type::Type=Any;
                  sub_args=Dict(),
                  output_fields=String[],
                  initfn=nothing,
                  retry=true,
                  subtimeout=0,
                  stopfn=nothing,
                  throw_on_execution_error=false)
```

`subscription_name`にサブスクライブし、受信した各結果に対して`fn`を実行し、`fn`が`true`を返すとサブスクリプションを終了します。

デフォルトでは、`fn`は`GQLReponse{Any}`を受け取り、個々の結果オブジェクトのデータは`gql_response.data[subscription_name]`で見つけることができます。

使用される場合、`initfn`はサブスクリプションがオープンになったときに一度呼び出されます。

サブスクリプションは`client`の`ws_endpoint`フィールドを使用します。

この関数は`do`キーワードと一緒に使用するように設計されています。

# 引数

  * `fn::Function`: 各結果に対して実行される関数で、サブスクリプションからの応答を受け取ります。サブスクリプションを閉じるかどうかを示すためにブール値を返す必要があり、`true`がサブスクリプションを閉じます。
  * `client::Client`: GraphQLクライアント（オプション）。指定されていない場合は、[`global_graphql_client`](@ref)が使用されます。
  * `subscription_name::Union{Alias, AbstractString}`: サーバーのサブスクリプション名。
  * `output_type::Type=Any`: サブスクリプション応答オブジェクトの出力データ型。`GQLResponse{output_type}`型のオブジェクトが返されます。詳細については、`GQLResponse`のドキュメントを参照してください。

# キーワード引数

  * `sub_args=Dict()`: サブスクリプション引数のキーと値のペアの辞書 - 辞書やベクターでネスト可能です。
  * `output_fields=String[]`: 返される出力フィールド。文字列、または辞書やベクターで構成されることができます。
  * `initfn=nothing`: サブスクリプションが初期化されたときに一度実行されるオプションの関数。
  * `retry=true`: サブスクリプションのオープンに失敗した場合に再試行します。
  * `subtimeout=0`: `stopfn`が指定されている場合、これは呼び出される期間です。`stopfn`が指定されていない場合、これはデータを待つためのタイムアウトです。タイマーは、各サブスクリプション結果が受信されるたびにリセットされます。
  * `stopfn=nothing`: `subtimeout`ごとに呼び出され、正の値を返すとサブスクリプションを停止する関数。タイマーは、各サブスクリプション結果が受信されるたびにリセットされます。
  * `throw_on_execution_error=false`: GraphQLサーバーの応答に実行中に発生したエラーが含まれている場合にエラーがスローされないようにするには、`true`に設定します。
  * `verbose=0`: 追加のログ記録のために1、2に設定します。

# 例

```julia
julia> open_subscription("subSaveUser", sub_args=Dict("role" => "SYSTEM_ADMIN")) do result
           fn(result)
       end
```

参照: [`GQLResponse`](@ref) ```
