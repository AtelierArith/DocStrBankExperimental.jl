```
async_execute(
    jl_conn::Connection,
    query::AbstractString,
    [parameters::Union{AbstractVector, Tuple},]
    binary_format::Bool=false,
    kwargs...
) -> AsyncResult
```

PostgreSQLデータベースでクエリを実行し、[`AsyncResult`](@ref)を返します。

`AsyncResult`には、クエリを非同期に処理する`Task`が含まれています。`AsyncResult`で`fetch`を呼び出すと、[`Result`](@ref)が返されます。

すべてのキーワード引数は[`execute`](@ref)と同じで、作成された`Result`に渡されます。

[`Connection`](@ref)上でアクティブにできる`AsyncResult`は1つだけです。複数の`AsyncResult`が同じ`Connection`を使用する場合、シリアルに実行されますが、順序の保証はありません。

`async_execute`はまだ[`Statement`](@ref)をサポートしていません。

`async_execute`はオプションで`parameters`ベクターを受け取り、クエリパラメータを文字列としてPostgreSQLに渡します。

`binary_format`がtrueに設定されている場合、データはバイナリ形式で転送されます。バイナリ転送のサポートは現在、基本データ型のサブセットに制限されています。

パラメータのないクエリは複数のSQLステートメントを含むことができ、最終ステートメントの結果が返されます。実行されたステートメント中に発生したエラーは、`CompositeException`にまとめられ、スローされます。

`Task`に通常のように、例外は`wait`または`fetch`を呼び出すときにスローされます。
