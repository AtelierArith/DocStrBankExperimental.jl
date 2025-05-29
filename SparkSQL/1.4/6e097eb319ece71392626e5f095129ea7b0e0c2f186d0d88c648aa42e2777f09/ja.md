# 目的

*Structured Query Language* (SQL)、*Data Manipulation Language* (DML)、および *Data Definition Language* (DDL) ステートメントを Apache Spark に送信します。

# 引数

  * `session:SparkSession`: SparkSession。Julia での作成方法については SparkSession ヘルプを参照してください。
  * `sqlText::String`: DDL、DML または SQL ステートメント。

# サポートされている DDL フォーマット:

  * ファイルフォーマット: CSV、JSON、arrow、parquet
  * データレイク: Hive、ORC、Avro
  * データレイクハウス: Delta Lake、Apache Iceberg。
  * クラウドオブジェクトストレージ: S3、Azure Blob Storage、Swift Object。

# 例

## CSV ファイルの例:

カンマ区切り値 (CSV) フォーマット。

```
stmt = sql(session, "SELECT * FROM CSV.`/pathToFile/fileName.csv`;")
```

## Parquet ファイルの例:

Apache Parquet フォーマット。

```
stmt = sql(session, "SELECT * FROM PARQUET.`/pathToFile/fileName.parquet`;")
```

## Delta Lake の例:

Delta Lake は Spark のためのオープンソースのストレージレイヤーです。Delta Lake は以下を提供します:

Spark における ACID トランザクション: シリアライズ可能な分離レベルにより、リーダーは常に不整合なデータを見ないことが保証されます。スケーラブルなメタデータ処理: Spark の分散処理能力を活用して、ペタバイト規模のテーブルに対するすべてのメタデータを数十億のファイルで簡単に処理します。

Delta Lake を使用するには、Delta Lake jar を Spark の jars フォルダに追加する必要があります。

以下の例は、Delta Lake と SparkSQL を使用したテーブルの作成 (DDL)、挿入 (DML)、および選択ステートメント (SQL) を示しています:

```
sql(session, "CREATE DATABASE demo;")
sql(session, "USE demo;")
sql(session, "CREATE TABLE tb(col STRING) USING DELTA;" )
```
