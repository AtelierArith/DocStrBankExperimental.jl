```
DBInterface.execute(db::SQLite.DB, sql::String, [params])
DBInterface.execute(stmt::SQLite.Stmt, [params])
```

任意の位置引数（`params`を`Vector`または`Tuple`として）または名前付き引数（`params`を`NamedTuple`または`Dict`として）を、`db`と`sql`で指定されたSQL文、またはすでに準備されたステートメント`stmt`にバインドし、クエリを実行して結果行のイテレータを返します。

返された結果行のイテレータは、単一パスの前方のみのイテレーションをサポートしています。`SQLite.reset!(result)`を呼び出すと、クエリが再実行され、イテレータが最初に戻ります。

結果セットイテレータは、[Tables.jl](https://github.com/JuliaData/Tables.jl)インターフェースをサポートしているため、`DataFrame(results)`、`CSV.write("results.csv", results)`など、任意のTables.jl互換のシンクに結果を収集できます。

`DBInterface.execute`に`strict=true`を渡すと、結果セットイテレータはSQLiteによって指定された正確な型の値を返すようになります。
