# 目的

Apache Spark クラスターに設定オプションを持つアプリケーションを送信します。

# 引数

  * `master::String`: Spark クラスターのマスターへの URL。
  * `appName::String`: アプリケーションの名前。
  * `config::Dict{String, String}()`: SparkSession のための1つ以上の設定オプション。

# 例

基本的なスパークセッション：

```
spark = SparkSession("spark://example.com:7077", "Julia SparkSQL Example App")
```

Hive 設定を持つスパークセッション：

```
spark = SparkSession("spark://example.com:7077", "Julia SparkSQL Example App", Dict{String,String}("spark.sql.warehouse.dir"=>"LOCATION","spark.sql.catalogImplementation"=>"hive"))
```

Delta Lake 設定を持つスパークセッション：

```
spark = SparkSession("spark://example.com:7077", "Julia SparkSQL Example App", Dict{String,String}("spark.sql.warehouse.dir"=>"LOCATION", "spark.sql.extensions"=>"io.delta.sql.DeltaSparkSessionExtension", "spark.sql.catalog.spark_catalog"=>"org.apache.spark.sql.delta.catalog.DeltaCatalog"))
```
