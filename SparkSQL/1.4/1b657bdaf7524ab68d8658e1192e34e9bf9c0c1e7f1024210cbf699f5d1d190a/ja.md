# 目的

Sparkデータを新しいJulia DataFrameに移動します。

# 引数

  * `ds:Dataset`: JuliaにDataFrameとしてインポートするApache Spark Dataset。

# データ型

この関数は、SparkデータからJulia DataFrameを作成する際に以下のデータ型をサポートしています：

  * `String`
  * `Date`
  * `Timestamp`
  * `integer`
  * `long`
  * `double`
  * `float`
  * `decimal`
  * `boolean`

# 追加要件

JuliaプログラムにDataFramesパッケージを含める必要があります。

`Using DataFrames`

Sparkデータに日付や小数が含まれている場合は、「Dates」と「Decimals」パッケージを含めてください。

`Using Dates, Decimals`

# 例

```
stmt = sql(session, "SELECT _c0 AS columnName1, _c1 AS columnName2 FROM CSV.`/pathToFile/fileName.csv`")
createOrReplaceTempView(stmt, "TempViewName")
sqlQuery = sql(session, "SELECT columnName1, columnName2 FROM TempViewName;")
juliaDataFrame = toJuliaDF(sqlQuery)
```
