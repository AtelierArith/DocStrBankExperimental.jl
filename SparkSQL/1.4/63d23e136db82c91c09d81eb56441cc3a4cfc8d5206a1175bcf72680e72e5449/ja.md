# 目的

Julia DataFrame のデータを Apache Spark の Dataset に移動します。

# 引数

  * `session::SparkSession`: Spark セッション。
  * `df::DataFrame`: Spark Dataset に移動する Julia DataFrame の名前。

# 例

この例では、Spark をクエリしてそのデータを Julia DataFrame に移動する方法を示します。次に、Julia で処理した後、データを再び Spark Dataset に移動します。

Spark から Julia DataFrame へ:

```
stmt = sql(session, "SELECT _c0 AS columnName1, _c1 AS columnName2 FROM CSV.`/pathToFile/fileName.csv`")
createOrReplaceTempView(stmt, "TempViewName")
sqlQuery = sql(session, "SELECT columnName1, columnName2 FROM TempViewName;")
juliaDataFrame = toJuliaDF(sqlQuery)
describe(juliaDataFrame)
```

Julia DataFrame のデータを Apache Spark Dataset に移動します。

```
sparkDataset = toSparkDS(sparkSession, juliaDataFrame)
createOrReplaceTempView(sparkDataset, "tempTable")
```

Dataset は区切り文字列です。列を生成するには、SparkSQL の "split" 関数を使用します。

```
sqlQuery = sql(sparkSession, "SELECT split(value, ',' )[0] AS columnName1, split(value, ',' )[1] AS columnName2 FROM tempTable")
```
