```
execute(
    {jl_conn::Connection, query::AbstractString | stmt::Statement},
    [parameters::Union{AbstractVector, Tuple},]
    throw_error::Bool=true,
    binary_format::Bool=false,
    column_types::AbstractDict=ColumnTypeMap(),
    type_map::AbstractDict=LibPQ.PQTypeMap(),
    conversions::AbstractDict=LibPQ.PQConversions(),
    not_null::Union{Bool, AbstractVector}=false,
) -> Result
```

PostgreSQLデータベースでクエリを実行し、`Result`を返します。`throw_error`が`true`の場合、クエリが致命的なエラーまたは読み取れない応答を返した場合にエラーをスローし、結果をクリアします。

クエリは`Connection`および`AbstractString`（SQL）引数として、または`Statement`として渡すことができます。

`execute`はオプションで`parameters`ベクターを受け取り、クエリパラメータを文字列としてPostgreSQLに渡します。

`column_types`は、結果の列に対する型のオーバーライドを受け入れ、`type_map`のものより優先されます。

`not_null`は、解析された列がnull値を含むことができるかどうかを示し、`missing`として解析されます。この引数は、すべての列に対する単一の`Bool`、`Bool`のリスト、または列名のリストであることができます。

`column_types`、`type_map`、および`conversions`引数に関する情報は、[Type Conversions](@ref typeconv)を参照してください。

`binary_format`がtrueに設定されている場合、データはバイナリ形式で転送されます。バイナリ転送のサポートは、現在基本データ型のサブセットに制限されています。
