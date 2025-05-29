```
db_table(database, table_name, athena_params, delta = false, iceberg = false, alias = "", df_name)
dt(database, table_name, athena_params, delta = false, iceberg = false, alias = "", df_name)
```

`db_table`は、メタデータとテーブルを追加して、基盤となるSQLクエリ構造を開始します。名前の代わりに直接`db_table`にパスが渡されると、それはメモリにコピーされるのではなく、ファイルから直接読み取られます。`db_table`は、テーブルへの直接ファイルパスのみをサポートします。DataFrameはビューとして読み取られます。`dbname.duckdb`や`dbname.sqlite`のようなデータベースファイルパスはサポートされていません。データベースファイルは、`connect(db, "path_to_db.duckdb")`を最初に使用して、`db_table`がデータベーステーブルを読み取れるようにする必要があります。

# 引数

  * `database`: データベースまたは接続オブジェクト
  * `table_name`: 文字列としてのテーブル名（データフレーム、名前、ローカルパス、またはURL）。     - CSV/TSV       - Parquet     - Json      - Iceberg     - Delta     - AWSまたはGoogle CloudのS3テーブル      - Google Sheetsスプレッドシートリンク

      * DuckDBとClickHouseは、パスとURLのベクトルをサポートしています。
      * DuckDBとClickHouseは、特定の場所にあるすべてのファイルタイプを読み取るために`*`ワイルドカードの使用もサポートしています。例えば：

          * `db_table(db, "Path/to/testing_files/*.parquet")`
      * 任意のDuckDBリーダー "read*csv('file*path', additional arguments allowed)" を使用します。
  * `delta`: デルタファイルを読み取るにはtrueでなければなりません
  * `iceberg`: iceberg finalize_ctesを読み取るにはtrueでなければなりません
  * `alias`: ファイルパスに`*`ワイルドカードを使用する際のオプション引数で、読み取られるデータのエイリアスをユーザーが決定できるようにします。空の場合、テーブルは`data`として参照されます。
  * `df_name`: DataFrameを第二引数として使用する場合、ビューの名前となる第三の文字列引数を提供する必要があります。

# 例

```jldoctest

julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> dt(db, df, "df_mem");

julia> db_table(db, "main.df_mem");

julia> dt(db, "df_mem" , alias = "my_table");
```
