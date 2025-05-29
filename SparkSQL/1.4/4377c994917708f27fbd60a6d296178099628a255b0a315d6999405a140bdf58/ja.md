# 目的

Spark Datasetをメモリにキャッシュします。

# 引数

  * `ds::Dataset`: キャッシュするDataset。

# 例

```
stmt = sql(session, "SELECT _c0 AS columnName1, _c1 AS columnName2 FROM CSV.`/pathToFile/fileName.csv`")
cache(stmt)
```
