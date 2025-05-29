# 目的

Apache Spark クラスターにアプリケーションを提出します。

# 引数

  * `master::String`: Spark クラスターのマスターへの URL。
  * `appName::String`: アプリケーションの名前。

# 例

基本的な Spark セッション:

```
spark = SparkSession("spark://example.com:7077", "Julia SparkSQL Example App")
```
