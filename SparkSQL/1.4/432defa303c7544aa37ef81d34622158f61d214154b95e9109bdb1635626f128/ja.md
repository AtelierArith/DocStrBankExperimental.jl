### About

SparkSQL.jlは、開発者がJuliaプログラミング言語をApache Sparkデータ処理エンジンと共に使用できるようにするソフトウェアです。

### Use Case

*構造化クエリ言語*（SQL）、*データ操作言語*（DML）、および*データ定義言語*（DDL）ステートメントをApache Sparkに送信します。SparkからJulia DataFramesにデータを移動し、Julia DataFrameデータをSparkに移動するための関数があります。

SparkSQL.jlは、ワークロード要件に合わせて計算ノードをスケールする動的な水平オートスケーリングなどの高度な機能を提供します。

このパッケージは、オンプレミスおよびクラウドのデータレイク、レイクハウス（Delta Lake、Iceberg）における構造化データおよび半構造化データをサポートしています。

# Available Functions

各関数のヘルプを見るには?を使用します。

  * `initJVM`: JuliaでJava仮想マシン（JVM）を初期化します。
  * `SparkSession`: 設定オプションを持つアプリケーションをApache Sparkクラスターに送信します。
  * `sql`: SQL、DDL、およびDMLステートメントをSparkに送信するための関数です。
  * `cache`: Sparkデータセットをメモリにキャッシュするための関数です。
  * `createOrReplaceTempView`: セッションの期間中持続する一時ビューを作成します。
  * `createGlobalTempView`: アプリケーションの期間中持続する一時ビューを作成します。
  * `toJuliaDF`: SparkデータをJulia DataFrameに移動します。
  * `toSparkDS`: Julia DataFrameデータをSparkデータセットに移動します。

SparkSQL.jlの計算ノードオートスケーリング機能はKubernetesに基づいています。Kubernetes上のSparkSQL.jlの手順については、kubernetes/README.mdを参照してください。

# Quick Start

### Install and Setup

Apache Spark 3.3.1以降をダウンロードし、SparkおよびJavaのホームの環境変数を設定します：

```
export SPARK_HOME=/path/to/apache/spark
export JAVA_HOME=/path/to/java
```

LinuxでOpenJDK 11を使用している場合は、processReaperUseDefaultStackSizeをtrueに設定します：

```
export _JAVA_OPTIONS='-Djdk.lang.processReaperUseDefaultStackSize=true'
```

### Startup

JVM相互運用のために必要な`"JULIA_COPY_STACKS=yes"`でJuliaを起動します：

```
JULIA_COPY_STACKS=yes julia
```

MacOSでは、"handle-signals=no"でJuliaを起動します：

```
JULIA_COPY_STACKS=yes julia --handle-signals=no
```

### Usage

JuliaでDataFramesパッケージを含めます。また、Sparkデータに日付や小数が含まれている場合は、DatesおよびDecimalsパッケージも含めます。

```
using SparkSQL, DataFrames, Dates, Decimals
```

JVMを初期化し、Sparkセッションを開始します：

```
initJVM()
sparkSession = SparkSession("spark://example.com:7077", "Julia SparkSQL Example App")
```

Sparkからデータをクエリし、Juliaデータセットにロードします。

```
stmt = sql(sparkSession, "SELECT _c0 AS columnName1, _c1 AS columnName2 FROM CSV.`/pathToFile/fileName.csv`")
createOrReplaceTempView(stmt, "TempViewName")
sqlQuery = sql(sparkSession, "SELECT columnName1, columnName2 FROM TempViewName;")
juliaDataFrame = toJuliaDF(sqlQuery)
describe(juliaDataFrame)
```

Julia DataFrameデータをApache Sparkデータセットに移動します。

```
sparkDataset = toSparkDS(sparkSession, juliaDataFrame,",")
createOrReplaceTempView(sparkDataset, "tempTable")
```

データセットは区切り文字付きの文字列です。列を生成するには、SparkSQLの"split"関数を使用します。

```
sqlQuery = sql(sparkSession, "Select split(value, ',' )[0] AS columnName1, split(value, ',' )[1] AS columnName2 from tempTable")
```

# Spark Data Sources

サポートされているデータソースには以下が含まれます：

  * ファイル形式：CSV、JSON、arrow、parquet
  * データレイク：Hive、ORC、Avro
  * データレイクハウス：Delta Lake、Apache Iceberg。
  * クラウドオブジェクトストレージ：S3、Azure Blob Storage、Swift Object。

## Data Source Examples

### CSV file example:

カンマ区切り値（CSV）形式。

```
stmt = sql(session, "SELECT * FROM CSV.`/pathToFile/fileName.csv`;")
```

### Parquet file example:

Apache Parquet形式。

```
stmt = sql(session, "SELECT * FROM PARQUET.`/pathToFile/fileName.parquet`;")
```

### Delta Lake Example:

Delta LakeはSparkのためのオープンソースのストレージレイヤーです。Delta Lakeは以下を提供します：

  * Spark上のACIDトランザクション：シリアライズ可能な分離レベルにより、リーダーは常に一貫性のないデータを見ないことが保証されます。
  * スケーラブルなメタデータ処理：Sparkの分散処理能力を活用して、ペタバイト規模のテーブルのすべてのメタデータを処理します。

例は、Delta LakeとSparkSQLを使用したテーブル作成（DDL）ステートメントを示しています：

```
sql(session, "CREATE DATABASE demo;")
sql(session, "USE demo;")
sql(session, "CREATE TABLE tb(col STRING) USING DELTA;" )
```

Delta Lake機能を使用するには、Delta LakeのjarをSparkのjarフォルダーに追加する必要があります。
