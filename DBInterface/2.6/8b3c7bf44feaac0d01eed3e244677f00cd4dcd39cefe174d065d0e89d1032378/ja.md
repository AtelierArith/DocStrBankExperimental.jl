```
DBInterface.execute(conn::DBInterface.Connection, sql::AbstractString, [params]) => DBInterface.Cursor
DBInterface.execute(stmt::DBInterface.Statement, [params]) => DBInterface.Cursor
DBInterface.execute(f::Callable, conn::DBInterface.Connection, sql::AbstractString, [params])
DBInterface.execute(f::Callable, stmt::DBInterface.Statement, [params])
```

データベースパッケージは、オプションの `params` 引数を取る有効な、準備された `DBInterface.Statement` サブタイプのために `DBInterface.execute` をオーバーロードする必要があります（最初のメソッドシグネチャは `DBInterface.prepare` を使用して DBInterface.jl で定義されています）。この `params` 引数は、位置パラメータ用のインデックス可能なコレクション（`Vector` または `Tuple`）または名前付きパラメータ用の `NamedTuple` である必要があります。あるいは、パラメータは `DBInterface.execute` のキーワード引数として指定することもできます。

`DBInterface.execute` は、有効な `DBInterface.Cursor` オブジェクトを返す必要があります。これは「行」のイテレータであり、それ自体はプロパティアクセス可能でなければなりません（すなわち、名前による値アクセスのために `propertynames` と `getproperty` を実装する必要があります）し、インデックス可能でなければなりません（すなわち、インデックスによる値アクセスのために `length` と `getindex` を実装する必要があります）。これらの「結果」オブジェクトは、インターフェースを満たす限り、明示的に `DBInterface.Cursor` をサブタイプ化する必要はありません。DDL/DML SQL ステートメントの場合、通常は結果を返さないため、`nothing` を反復するだけのイテレータが返されることが期待されます。つまり、「空の」イテレータです。

`DBInterface.execute` は **単一の** `DBInterface.Cursor` を返すことに注意してください。これはデータベースからの単一の結果セットを表します。単一のクエリからの複数の結果セットを含むユースケースについては、`DBInterface.executemultiple` を参照してください。

関数 `f` が提供されると、`DBInterface.execute` は `DBInterface.Cursor` オブジェクトに `f` を適用した結果を返し、終了時に準備されたステートメントを閉じます。
