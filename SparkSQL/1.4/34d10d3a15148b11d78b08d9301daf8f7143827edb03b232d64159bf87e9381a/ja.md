# 目的

Apache Spark クラスター上に、Spark アプリケーションの期間中に一時的なデータベースビューを作成します。

# 引数

  * `ds:Dataset`: セッションデータベースビューを作成するための Spark DataSet。
  * `tempViewName::String`: ビューの名前。

# 例

```
stmt = sql(session, "SELECT * FROM CSV.`/pathToFile/fileName.csv`")
createGlobalTempView(stmt, "TempViewName")
count = sql(session, "SELECT COUNT(*) AS total FROM TempViewName;")
```
